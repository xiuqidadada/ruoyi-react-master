## 使用 docker 进行快速部署

1. 在项目路径下执行 `mvn clean package` 完成所有后端项目的编译构建，生成 jar 产物。

2. 在 `./docker` 路径下执行 `copy.sh`，将 docker 依赖的文件复制到 `./docker` 对应路径下。

3. 在 `./docker` 路径下执行 `deploy.sh`，完成 docker 镜像的构建和部署。

## 注意

为了使 docker 容器中的服务能够正常的访问其他 docker 容器中的服务，`docker-compose.yml` 中在一些环境变量中配置了 `172.17.0.1` 这个 ip 地址。这个 ip 地址是 docker0 虚拟网卡下宿主机的地址。这个地址在 linux 中有效，而在 win/mac 中，[docker-desktop] (https://www.docker.com/products/docker-desktop/)是通过虚拟机运行的 docker，需要使用 `host.docker.internal` 来代替。