#####1.这是神马？
 >这是一个提供公共配置的server。  
 * 它有自己的配置文件，其中写的配置内容包括：服务器所需要的公共配置信息，比如：服务端口，数据库链接信息等；  
 * 还有一些放在远程仓库的配置信息，其内容可以是业务上的一些属性，将其写成配置信息。
（选择将这些配置信息放在远程仓库，而不是放在服务中的某个配置文件中，是因为如果放在server的配置文件中，如果需要更改这些配置信息，那么server就需要重新打包、run；而写在远程仓库，在server的配置中引入链接等配置去读取远程库中的配置内容，即使内容改变了，server在每次去获取远程库中的内容时，也会读取到最新的配置信息，不需要重新run server。）


#####2.为什么要有这个？
* 可以提供给其他server需要的公共配置信息，及服务调用时的调用信息
* 提供业务中需要的配置信息
* 它是一种服务发现的实现方案，这里记录了分布式系统中所有服务的信息，开发者或者其他服务可以据此找到这些服务。



#####3.用这个有很么好处？
* 提供公共统一的配置信息
* 配置简单，无需了解其他服务的体系架构，就能找到并使用该服务
* 可以查询所有服务状态和集中控制所有服务的作用

out of scope：
分布式系统：
* 将整个软件视为一个系统
* 将整个系统分割成一系列的process（进程），每个process完成一定的功能
* 将这些process分散到不同的机器上，然后使用各种通信协议把它们链接起来



## 下载RabbitMQ镜像 
``` docker pull rabbitmq:management ``` 
## 启动RabbitMQ 
``` docker run -d --name uwo-rabbitmq --publish 5671:5671 --publish 5672:5672 --publish 4369:4369 --publish 25672:25672 --publish 15671:15671 --publish 15672:15672 rabbitmq:management ```
 
## 设置默认用户与密码 
``` docker run -d --name uwo-rabbitmq -e RABBITMQ_DEFAULT_USER=uwo -e RABBITMQ_DEFAULT_PASS=yan5845hao rabbitmq:management ``` 

## 设置默认的vhost 
``` docker run -d --name uwo-rabbitmq -e RABBITMQ_DEFAULT_VHOST=uwo rabbitmq:management ```
 ## 运行的界面地址 
 ``` http://10.211.55.8:15672/ ```





    
 
 