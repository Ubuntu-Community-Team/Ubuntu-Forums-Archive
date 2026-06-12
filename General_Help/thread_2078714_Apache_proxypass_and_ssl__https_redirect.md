---
title: "Apache proxypass and ssl / https redirect"
date: 2012-10-31
forum: General Help
---

### Post by asteway on 2012-10-31
Dear all,

I have configured a self signed SSL on my Ubuntu server and I use permanent redirect to redirect the http (:80) to https (:443). That is I added

```
Redirect permanent / https://foo.bar
```in my /etc/apache2/sites-available/default file.

Now I have installed an application that runs on tomcat on the same server that is [http://foo.bar:8080/app](http://foo.bar:8080/app) and I wanted to setup apache proxypass to tomcat. So I created an app.conf under /etc/apache2/conf.d/ that looks like
```

ProxyRequests Off
ProxyPreserveHost On
SSLProxyEngine On
<Proxy *>
    Order allow,deny
    Allow from all
</Proxy>

ProxyPass /app  http://localhost:8080/app
ProxyPassReverse /app  http://localhost:8080/app


```and now my tomcat application works perfectly on [http://foo.bar/app](http://foo.bar/app) but the redirection to https stops working. I want apache to do a proxypass to [https://foo.var/app](https://foo.var/app). I tried doing 

ProxyPass /app  [https://localhost:8080/app](https://localhost:8080/app)
ProxyPassReverse /app  [https://localhost:8080/app](https://localhost:8080/app)

but does not work.

---

### Post by asteway on 2012-11-01
Anyone?

---

