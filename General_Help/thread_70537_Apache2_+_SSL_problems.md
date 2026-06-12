---
title: "Apache2 + SSL problems"
date: 2005-09-30
forum: General Help
---

### Post by OldGaf on 2005-09-30
Hi,
I have apache2 istalled.
I can get to my default index page, but can't get to my HTTPS page - "The page cannot be displayed"
A few questions:
1) I do not plan on having Virtual sites.... is there a way of installing Apache so it does not have any of those configuration files (just to keep it simpler)
2) If I MUST deal with these files, (/sites-enabled/default + ssl) can anyone tell me what they should look like.
Here is my ssl:
NameVirtualHost *
<VirtualHost *>
ServerAdmin webmaster@localhost
ServerName [www.my-domain.com:443](www.my-domain.com:443)
DocumentRoot /var/www/
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
# Commented out for Ubuntu
#RedirectMatch ^/$ /apache2-default/
</Directory>
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
AllowOverride None
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
</Directory>
ErrorLog /var/log/apache2/error.log
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem
CustomLog /var/log/apache2/access.log combined
ServerSignature On
Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
</VirtualHost>
Here is my apache2 error log:
[Fri Sep 30 11:05:43 2005] [notice] caught SIGTERM, shutting down
[Fri Sep 30 11:05:45 2005] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Fri Sep 30 11:05:46 2005] [notice] Apache/2.0.53 (Ubuntu) PHP/4.3.10-10ubuntu4.1 mod_ssl/2.0.53 OpenSSL/0.9.7e configured -- resuming normal operations
As I said, my HTTP works, but HTTPS returns "The page cannot be displayed".
netstat -tapn gives me this:
tcp6       0      0 :::80                   :::*                    LISTEN     4521/apache2
tcp6       0      0 :::443                  :::*                    LISTEN     4521/apache2
Any help would be great... I have already wasted days on this that could have been spent on development.:confused:

---

### Post by OldGaf on 2005-10-01
Fixed it..... thanks for your help....... mmmm......
For those who need help with this but are not getting any replys,

NameVirtualHost *
<VirtualHost *>
ServerAdmin webmaster@localhost
ServerName [www.my-domain.com:443](www.my-domain.com:443)

Should be:

NameVirtualHost *:443
<VirtualHost *:443>
ServerAdmin webmaster@localhost
ServerName [www.my-domain.com:443](www.my-domain.com:443)

---

