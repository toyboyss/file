教程使用 VINGA 的博客 的docker部署方法，特点是特别简单，快速，因此本站不演示手动搭建教程。

对接前需要三个参数：节点id 服务器ip 数据库信息（数据库名、用户名、密码）

安装步骤
1.安装 docker

docker version > /dev/null || curl -fsSL get.docker.com | bash
service docker restart
webapi 方式对接:

docker run -d --name=ssrmu -e NODE_ID=节点ID -e API_INTERFACE=modwebapi -e WEBAPI_URL=需要对接的地址 -e WEBAPI_TOKEN=前端设置的token --network=host --log-opt max-size=50m --log-opt max-file=3 --restart=always fanvinga/docker-ssrmu
数据库方式对接：

docker run -d --name=ssrmu -e NODE_ID=节点ID -e API_INTERFACE=glzjinmod -e MYSQL_HOST=MYSQL地址 -e MYSQL_USER=mysql用户名 -e MYSQL_DB=数据库名 -e MYSQL_PASS=数据库密码 --network=host --log-opt max-size=50m --log-opt max-file=3 --restart=always fanvinga/docker-ssrmu
本站示例：

docker run -d --name=ssrmu -e NODE_ID=3 -e API_INTERFACE=glzjinmod -e MYSQL_HOST=23.94.24.115 -e MYSQL_USER=sspanel -e MYSQL_DB=sspanel -e MYSQL_PASS=数据库密码 --network=host --log-opt max-size=50m --log-opt max-file=3 --restart=always fanvinga/docker-ssrmu
备注：从对接角度而言，第一个节点设置好了，其余节点安装非常简单，只需修改节点ID数字即可，其余都不用管。
