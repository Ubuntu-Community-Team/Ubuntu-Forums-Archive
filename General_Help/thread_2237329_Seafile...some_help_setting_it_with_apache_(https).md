---
title: "Seafile...some help setting it with apache (https) + MySQL?"
date: 2014-08-01
forum: General Help
---

### Post by timonoj on 2014-08-01
Hi guys,

I'm trying to setup Seafile with apache2 and mysql, but I want it in order to be in an apache domain folder, not being the main one. I'd like seafile web to run in a special port (such as 8000 or similar), while I keep the 80 for a different site. Is it possible? How should I set it? I did something wrong at some point, as I think apache is listening to the wrong port and the browser connection gets rejected.

Thanks!

---

### Post by TheFu on 2014-08-02
Use a virtualhost. [https://httpd.apache.org/docs/2.2/vhosts/](https://httpd.apache.org/docs/2.2/vhosts/)  Be certain to use the documents for the version of apache on your system.  14.04 uses 2.4, I think.

---

### Post by timonoj on 2014-08-05
Thanks! I followed this one:
[http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html), as there's no examples for 2.4. Anyway, not that much that I changed. I intend to run first on http:8090 then on 8091 for https (I'll focus on http first, as it's already giving me issues).
000-default.conf:
```

<VirtualHost *:8090>
        ServerName my_ddns_domain
        Alias /media  /media/data/seafile/timonoj/seafile-server-latest/seahub/media
        RewriteEngine On

        <Location /media>
                Require all granted
        </Location>
        #
        # seafile fileserver
        #
        ProxyPass /seafhttp [http://127.0.0.1:8082](http://127.0.0.1:8082)
        ProxyPassReverse /seafhttp [http://127.0.0.1:8082](http://127.0.0.1:8082)
        RewriteRule ^/seafhttp - [QSA,L]
        #
        # seahub
        #
        RewriteRule ^/(media.*)$ /$1 [QSA,L,PT]
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^(.*)$ /seahub.fcgi$1 [QSA,L,E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
</VirtualHost>

```

apache2.conf:
```

FastCGIExternalServer /var/www/seahub.fcgi -host 127.0.0.1:8000

```
I added Listen 8090 on ports.conf.

The page loads, but it renders incorrectly, missing most of the format and all the images:
[IMG]http://i.imgur.com/QOrwax5.jpg[/IMG]

It looks to be functional, as I could even log in....Any idea of what I'm doing wrong? I'm at a loss here...

EDIT: Could it be the /media alias? Can I name the alias anything else than /media? Right now my data HDD for seacloud is mounted on the /media folder, just as ubuntu usually does.
Thanks a million!


EDIT2: Goddammit, it was indeed the /media mapping! How would they want to do an alias of a common ubuntu folder! I created a second root folder for mounting stuff, it seems to load now.

---

