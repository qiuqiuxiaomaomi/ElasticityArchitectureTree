# ElasticityArchitectureTree
弹性架构设计

<pre>
网站架构的伸缩性分为两类：

      1：根据功能进行物理分离实现伸缩，垂直拆分  （业务拆分）
      2：单一功能通过集群实现伸缩，水平拆分   （集群部署）   
</pre>

<pre>
应用服务器集群的伸缩性设计：

      1） HTTP重定向负载均衡
          HTTP重定向服务器是一台普通的应用服务器，其唯一的功能就是根据用户的HTTP请求计算
          一台真实的Web服务器地址，并将该Web服务器地址写入HTTP重定向响应中（响应状态码
          302）返回给用户浏览器。

            优点：简单
            缺点：浏览器需要两次请求服务器才能完成一次访问，性能较差；

            使用HTTP302响应码重定向，有可能使搜索引擎判断为SEO作弊，降低搜索排名。

      2）DNS域名解析负载均衡
         利用DNS处理域名解析请求的同时进行负载均衡处理的一种方案。

         优点：将负载均衡的工作交给DNS，省掉了网站管理维护负载均衡服务器的麻烦，同时许多
         DNS还支持基于地理位置的域名解析，即会将域名解析成距离用户地理最近的一个服务器地
         址，这样可以加速用户访问速度，改善性能。

      3）反向代理负载均衡
         缺点：反向代理服务器是所有请求和响应的中转站，其性能可能会成为瓶颈。

      5）IP负载均衡
         在网络层通过修改请求目标地址进行负载均衡。
</pre>