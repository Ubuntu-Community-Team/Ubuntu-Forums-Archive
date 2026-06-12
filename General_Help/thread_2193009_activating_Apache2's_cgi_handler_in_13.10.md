---
title: "activating Apache2's cgi handler in 13.10"
date: 2013-12-10
forum: General Help
---

### Post by Random Bob on 2013-12-10
solution:
> a2enmod cgid
between <Directory> tags, added line: AddHandler cgi-script .cgi
to each file in sites-available

can't seem to delete this topic; oh well...

original post:

I migrated my web server from an old 32-bit system to a slightly newer 64-bit one.  In the process I decided to perform a fresh install of Ubuntu 13.10, replacing a system that was incrementally upgraded from ~10.X.  I copied the data to the new web content folder, copied over the sites-available, and dropped httpd.conf into conf-available and enabled it.  When I access any of the (sub)domains, apache2 pulls up the appropriate cgi file.  However, all I get back is the text of the file, and it fails to execute.  The file cgi files' permissions are 500 for www-data: (same as before).  Setting permissions to 700 or 777 didn't change anything.

httpd.conf contains the line
```
AddHandler cgi-script .cgi
```
plus ServerName and other boring stuff.

an example site conf file, here is 000-default:
```
<VirtualHost *:80>
        ServerName www._____.com
        DocumentRoot /var/www/forum/
        DirectoryIndex index.cgi
        <Directory /var/www/forum/>
                Options Indexes FollowSymLinks MultiViews ExecCGI
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
        ErrorLog /var/www/logs/error_forum.log
        LogLevel info
</VirtualHost>

```

Am I missing something that is necessary in the newer versions, or could there be some other problem?  As I mentioned, I can access the cgi files via the web; the server just fails to run them.

---

