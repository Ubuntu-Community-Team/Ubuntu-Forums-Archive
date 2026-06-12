---
title: "ocs inventory with deployment"
date: 2007-08-06
forum: General Help
---

### Post by dpgrent on 2007-08-06
Problems Installing OCS inventory with Package Deployment

have setup ocs fine on vmware esx3 with ubuntu server 7.04 
have got all of ocs working and can now autodeploy agent ( will be to over 600 machines in our company) with combination of linux and windows machines and servers

just having a lot of problems getting auto deployment working

have apache2 installed with all php5 mysql5 etc all addition dependencies for server installation

but having a huge problem with getting ssl working on machine

ocs requires both http and https working.

two main folders var/www/ocsreports which is purely http
var/www/download which requires both http and https

using self signed to test will register once get playing correctly

have copied /etc/apache2/sites-available/default to ssl and put ports in 80 in default and 443 in ssl
default 

NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
#        SSLEngine off
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>


ssl file 

NameVirtualHost *:443
<VirtualHost *:443>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        SSLEngine On
     #   SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire

        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

now getting an error when trying to browse to [https://myserver/download](https://myserver/download) in firefox is 

error 12263 
have already redone ssl certs self signed . 

Please help not sure where to go next ocs forums have told me to make ssl optional not sure how to do this.

if any requires any other information let me know can post any error logs etc if required.

---

