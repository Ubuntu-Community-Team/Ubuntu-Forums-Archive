---
title: "Apache ProxyPass &amp; SSL"
date: 2015-05-09
forum: General Help
---

### Post by scambro on 2015-05-09
I'm having a hard time grasping this concept and wasn't sure the best forums for Apache content...

I have a virtual server (server01) that catches all incoming traffic on ports 80 and 443.  That server has an Apache service on it, for both ports 80 and 443.  I recently added a second virtual server (server02) to handle a specific service, so I spun up a VBox image with Ubuntu on it, installed Apache, and I could access it fine on other ports (8080, 8443, for example).  I setup a Rewrite rule that moves requests on port 8080 over to 8443, worked great.  But I wanted to learn about ProxyPass and run this second server on a subdomain instead, so I changed the second server back to ports 80/443, changed the rewrite rules and internally had no issues.  Then I moved back to the main outside server running on port 80 and configured a VirtualHost for the new subdomain.  

My new conf file on server01 looks like this:

```
<VirtualHost *:80>
        ServerName server02.domain.com
        ProxyRequests off
        <Proxy *>
                Order deny,allow
                Allow from all
        </Proxy>
        ProxyPreserveHost on
        ProxyPass / http://server02/
        ProxyPassReverse / http://server02/
</VirtualHost>
```

Works, but, what's happening is I go to server02.domain.com on port 80, that hits server01 first then I get proxied over to server02:80, which has a redirect rule that then moves me to server02.domain.com:443.  That request hits server01, and it's routing me to the main server01:443 pages.  My conf file on server02 looks like this:

```
<VirtualHost *:80>
  RewriteEngine on
  RewriteCond %{SERVER_PORT} !^443$
  RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [NC,R,L]
etc, etc
</VirtualHost>
<VirtualHost *:443>
  ssl certs, etc
</VirtualHost>
```

I must be missing something in the configuration of server01 where if I get a server02.domain.com:443 request, that it forwards it to server02:443, but I can't seem to get that work without just crashing apache.  I've copied my .pem file from server02 to server01's ssl directory and tried to add it to the apache conf files, but I'm doing something very wrong when I try that because apache won't even start then.

Does this even make sense...  Thanks!

---

### Post by scambro on 2015-05-10
FYI - for the help of anyone else who came across this, I resolved it with the help of thread [http://ubuntuforums.org/showthread.php?t=2064909](http://ubuntuforums.org/showthread.php?t=2064909).  My SSL config file on server01 now looks like this:

```

<VirtualHost *:443>
  ServerName server02.the-hoyts.com:443

  SSLEngine on
  SSLProxyEngine on
  SSLProxyVerify none
  SSLProxyCheckPeerCN off
  SSLProxyCheckPeerName off
  SSLProxyCheckPeerExpire off

  ProxyRequests off
  ProxyPreserveHost On
  SSLCertificateFile /etc/apache2/ssl/server02.pem
  SSLCertificateKeyFile /etc/apache2/ssl/server02.key

  ProxyPass / https://server02/
  ProxyPassReverse / https://server02/
</VirtualHost>

```

---

