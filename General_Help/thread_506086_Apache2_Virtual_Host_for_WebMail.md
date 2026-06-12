---
title: "Apache2 Virtual Host for WebMail"
date: 2007-07-21
forum: General Help
---

### Post by dir7bag on 2007-07-21
I am attempting to get a Citadel install working.  I can access the Citadel web interface at [http://domain.tld: port](http://domain.tld: port), but I cannot seem to get the Virtual Host to let me access [http://mail.domain.tld](http://mail.domain.tld).  Any help is appreciated.

I have an MX setup for host: mail.domain.tld; preference: 5; data: domain.tld

Contents of httpd.conf
```
NameVirtualHost *:80

<VirtualHost *:80>
        DocumentRoot /var/www
        ServerName www.domain.tld
</VirtualHost>

<VirtualHost *:80>
    ServerName mail.domain.tld
    ProxyPass / http://127.0.0.1:8504/
    ProxyPassReverse / http://127.0.0.1:8504/
</VirtualHost>
```

Contents of proxy.conf
```
<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests On

        <Proxy *>
                AddDefaultCharset Off
                Order deny,allow
                Deny from all
                Allow from 192.168.2.10
        </Proxy>

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>
```

---

