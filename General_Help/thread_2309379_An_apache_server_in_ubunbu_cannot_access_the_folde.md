---
title: "An apache server in ubunbu cannot access the folder mounted by mount a CIFS folder"
date: 2016-01-10
forum: General Help
---

### Post by csshih on 2016-01-10
Hello everyone
I used “mount cifs” to mount a folder.
According to the request of users, I need to install an apache as a http file server.
Then, I use symbolic link, linked all the CIFS folder to /var/www/html
I add one in /etc/fstab:
“//10.11.11.11/public /CIFS cifs username=smbuser,password=smbuser,uid=www-data,gid=www-data,iocharset=utf8 0 0” to mount this CIFS folder.
I can use command line to access this folder.
However, the apache server cannot link to this CIFS folder.
The log is 
“AH00037: Symbolic link not allowed or link target not accessible: /var/www/html/package”
 
I add this in apache2.conf:
```
<Directory /var/www/html>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
#       Options Indexes FollowSymLinks
#       AllowOverride None
#       Require all granted
</Directory>
 
```
In “/etc/apache2/sites-enabled/ssl.conf”
 
I add this config:
```
<IfModule mod_ssl.c>
        <VirtualHost _default_:443>
                ServerAdmin webmaster@localhost
 
                DocumentRoot /var/www/html
 
        DocumentRoot /var/www/html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
```
 
Ps: I also try to use Alias in apache, but I met the same error log while access the deeper folder under the folder setting in “Alias”
 
Is anyone can give me an idea?

---

### Post by SeijiSensei on 2016-01-10
Rather than linking, try making the DocumentRoot point directly to the mounted file share.

Also you shouldn't muck with apache2.conf.  Edit the virtual host configurations in /etc/apache2/sites-available/ instead.  Please read this: [https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

---

### Post by csshih on 2016-01-10
hi SeijiSensei

thanks for your suggestion

I modified apache2.conf back to the original setting

And I also change /etc/apache2/sites-enabled/ssl.conf

(which is symbolic link to sites-availabled)

```
        DocumentRoot /mnt/smbfs/
       <Directory /cifs/>
                Options Indexes FollowSymLinks
                AllowOverride All
                Order allow,deny
                Allow from all
        </Directory>

```
However, in /var/log/apache2/error.log

The error message is 
```

[Mon  Jan 11 10:22:38.884667 2016] [authz_core:error] [pid 2896:tid  2974767936] [client 172.19.150.74:55001] AH01630: client denied by  server configuration: /mnt/smbfs/cifs

```
Here is some more information:

the APACHE_RUN_USER=builder, and the folder "cifs" owner is builder

Thank you very much

---

### Post by csshih on 2016-01-10
hi sir
I use your idea to modifed ssl.conf
to 
        <Directory /cifs/>
                Options Indexes FollowSymLinks
                AllowOverride none
#                Order allow,deny
#               Allow from all
                Require all granted

And it works
Thanks your help very much.
Best regards,
Stuart Shih

---

