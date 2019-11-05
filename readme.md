### 如何编写web服务器


WEB服务器也叫网页服务器（Web server),主要功能：

```text
解析HTTP协议，当web server收到一个HTTP请求,会返回一个HTTP响应。HTTP回复一般包含一个HTML文件，有时也可以包含纯文本文件、图像或其他类型的文件。
```


http server 需要实现基本功能：
```text
1.监听http 请求(request)
 a. 创建tcp/ip socket
 b. 绑定socket地址(ip:port)
 c. 开启监听

2.处理http 请求(response)
  a. 等待一个客户端连接
  b.读取客户端请求信息
  c.执行业务处理函数 httpHanler
  d.服务端响应数据给请求的客户端
  e.关闭连接
```



请求、响应日志
```bash
-------------------------------------------|
---------receive data from client----------|
-------------------------------------------|
GET /favicon.ico HTTP/1.0
Host: localhost:5000
Connection: close
Pragma: no-cache
Cache-Control: no-cache
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.70 Safari/537.36
Accept: image/webp,image/apng,image/*,*/*;q=0.8
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: no-cors
Referer: http://localhost:5000/
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7


-------------------------------------------|
------sending data back to the client------|
-------------------------------------------|

HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: http-server/1.2.0 (myserver)
Last-Modified: Wed, 22 Jul 2019 19:00:00 GMT
Content-Length: 148
Content-Type: text/html
Connection: Closed

<html>
    <head>
        <title>http server example</title>
    </head>
    <body>
        <h1>The HTTP Server is working!</h1>
    </body>
</html>
```