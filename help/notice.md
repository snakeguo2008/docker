###  1）docker将本地文件映射到容器之后，在容器里面的修改会被实现到容器外部

###  2) docker run -i -v /root/gocode:/go gobuildenv:1.0.0  rm -rf  `/go`/src/github.com/robfig

###  3）手动删除空悬镜像命令
*  `docker rmi $(docker images --quiet --filter "dangling=true")`

### 4）当docker运行久了之后会有很多不被使用的镜像，可以使用如下命令去查询
* `docker system df`
* 可以使用以下命令去删除
* `docker system df -v` 命令可以进一步查看空间占用细节，以确定是哪个镜像、容器或本地卷占用过高空间


* 自动清理命令
```
  docker system prune
  docker system prune后可以加额外的参数，如：
  docker system prune -a ： 一并清除所有未被使用的镜像和悬空镜像。
  docker system prune -f ： 用以强制删除，不提示信息。
  docker image prune：删除悬空的镜像。

  docker container prune：删除无用的容器。
      --默认情况下docker container prune命令会清理掉所有处于stopped状态的容器
      --如果不想那么残忍统统都删掉，也可以使用--filter标志来筛选出不希望被清理掉的容器。例子：清除掉所有停掉的容器，但24内创建的除外：
      --$ docker container prune --filter "until=24h"  

  docker volume prune：删除无用的卷。
  docker network prune：删除无用的网络

```
