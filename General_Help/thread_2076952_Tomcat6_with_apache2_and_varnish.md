---
title: "Tomcat6 with apache2 and varnish"
date: 2012-10-27
forum: General Help
---

### Post by smsmail on 2012-10-27
I am having trouble getting tomcat6 and solr working on my website server.  It is a linode server runnning Ubuntu 10.04 LTS.  I have apache2 running with Varnish as a cache for the Drupal 7 site the server is hosting.

from my apache2/ports.conf
```
NameVirtualHost *:8080
Listen 8080

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```


from the sites-available file for the site.
```
<VirtualHost *:8080>

   ServerName serviidb.com

   ServerAlias www.serviidbgroup.info serviidb.com www.serviidb.com serviidbgroup.info

   ServerAdmin webmaster@serviidb.com
   JkMount /* default

   DocumentRoot /var/www/serviidb.com/html


</VirtualHost>

```

from varnish's default.vcl

```
# Default backend definition.  Set this to point to your content
# server.
#
backend default {
  .host = "127.0.0.1";
  .port = "8080";
}

```

from tomcat6 server.xml

```
  <!-- A "Connector" represents an endpoint by which requests are received
         and responses are returned. Documentation at :
         Java HTTP Connector: /docs/config/http.html (blocking & non-blocking)
         Java AJP  Connector: /docs/config/ajp.html
         APR (HTTP/AJP) Connector: /docs/apr.html
         Define a non-SSL HTTP/1.1 Connector on port 8080
    -->
    <Connector port="8080" protocol="HTTP/1.1" 
               connectionTimeout="20000" 
               URIEncoding="UTF-8"
               redirectPort="8443" />
    <!-- A "Connector" using the shared thread pool-->
    <!--
    <Connector executor="tomcatThreadPool"
               port="8080" protocol="HTTP/1.1" 
               connectionTimeout="20000" 
               redirectPort="8443" />

```

Tomcat6 starts but I cannot get solr to work, I cannot figure a way to make sure tomcat6 is working properly.

Any help would be apprciated.

---

