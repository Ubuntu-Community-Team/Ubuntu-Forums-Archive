---
title: "Forbidden Access on apache2.4.7"
date: 2015-05-07
forum: General Help
---

### Post by risva on 2015-05-07
Hello all,
i know a number of similar questions have been asked and answered, but i have tried all given suggestions/answers but non have helped!!
i am running an Apache2..4.7 on ubuntu 14.4, i've mkdir /var/www/html/download and cp src /var/www/html/download/file.extn
while the request localhost or 127.0.0.1 and surprisingly 127.0.1.1 are returning Ubuntu default page, 
[http://127.0.0.1/download/file.extn](http://127.0.0.1/download/file.extn) is giving 
> 
**Forbidden**

 You don't have permission to access /download/file.extn on this server.

 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at 127.0.0.1 Port 80

error log says
> (13)Permission denied: [client 127.0.0.1:52345] AH00035: access to /download/apkFile.apk denied (filesystem path '/var/www') because search permissions are missing on a component of the path

apache2.conf has been changed to :
> 
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

<Directory /usr/share>
    AllowOverride None
    Require all granted
</Directory>

<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

<Directory /var/www/html/download/>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

and permission to all directories leading to /var/www/html/download/file.extn has been chmod to 644

please suggest remedy.....Thanks!

---

### Post by SeijiSensei on 2015-05-07
The "user" www-data must own all the files in the website directories, or have read and list privileges for them.  If "search permissions" are missing then one of the directories in the path, probably /downloads/, does not have eXecute privilege set correctly. 

Make sure all the directories have at least 711 permissions, and all the files have 644 privileges.

---

### Post by risva on 2015-05-07
Thanks SeijiSensei,

it worked!! I've given all directories 755 and files 644. thanks once again!

---

