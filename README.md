# helm-chart

## helm的chart仓库地址为：https://panzhen6668.github.io/helm-chart
参考技术文档: https://www.jianshu.com/p/04b2dbc7b59f
## 本Chart仓库的使用方法

1、添加chart仓库
```
# helm repo add hpz_repo https://panzhen6668.github.io/helm-chart
```

2、添加成功
```
# helm repo list
NAME  	URL                                   
myrepo	https://panzhen6668.github.io/helm-chart
```

3、搜索chart包
```
# helm search repo
NAME                              	CHART VERSION	APP VERSION	DESCRIPTION                                   
hpz_repo/edgex                      	0.1.0        	1.0        	A Helm chart for EdgeX Geneva                 
hpz_repo/kubernetes-dashboard       	2.3.0        	2.0.3      	General-purpose web UI for Kubernetes clusters
hpz_repo/test                       	0.1.0        	1.16.0     	A Helm chart for Kubernetes 
```

4、安装chart包
```
# helm install 自定义releasename hpz_repo/test
# 最后一个参数hpz_repo/test可以是本地文件夹,也可以是远程仓库
```

5、查看应用状态
```
# helm list
[root@master01 github.com]# helm list
NAME            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                   APP VERSION
hpz-nginx-f     default         5               2021-09-08 18:30:55.429190112 +0800 CST deployed        nginx-test-0.1.0        1.16.0
testchart       default         1               2021-09-09 15:16:46.071531433 +0800 CST deployed        test-0.1.0              1.16.0
 
# helm status releaseName

[root@master01 github.com]# helm status testchart
NAME: testchart
LAST DEPLOYED: Thu Sep  9 15:16:46 2021
NAMESPACE: default
STATUS: deployed
REVISION: 1
NOTES:
1. Get the application URL by running these commands:
  export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=test,app.kubernetes.io/instance=testchart" -o jsonpath="{.items[0].metadata.name}")
  export CONTAINER_PORT=$(kubectl get pod --namespace default $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
  echo "Visit http://127.0.0.1:8080 to use your application"
  kubectl --namespace default port-forward $POD_NAME 8080:$CONTAINER_PORT
```


