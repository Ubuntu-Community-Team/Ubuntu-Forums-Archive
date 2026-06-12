---
title: "apache, how to set virtual directory?"
date: 2005-04-19
forum: General Help
---

### Post by jcdotnet on 2005-04-19
I just move from iis .

I would like to know how can i set virtual directory in apache ( alias name)

example:  I save my html file to /home/jc/web1
then i need to browse my web via  [http://localhost/web1](http://localhost/web1)



Thanks
JC

---

### Post by Nano on 2005-04-19
[QUOTE=jcdotnet]I just move from iis .

I would like to know how can i set virtual directory in apache ( alias name)

example:  I save my html file to /home/jc/web1
then i need to browse my web via  [http://localhost/web1](http://localhost/web1)



Thanks
JC[/QUOTE]
 I recommend you to use the default directory convention and store your web files under:
/var/www/
which will be your [http://localhost/](http://localhost/) by default.

---

### Post by speedman on 2005-04-19
I am assuming you are using Apache 2.  If so, create an alias file in /etc/apache2/conf.d as follows:

=====

Alias web1 /home/jc/web1

<Directory /home/jc/web1>
DirectoryIndex index.html
Options FollowSymLinks
AllowOverride None
order allow,deny
allow from all
</Directory>

=====

Then reload apache to parse your new config:

/etc/init.d/apache2 reload


Regards,

SM

---

### Post by jcdotnet on 2005-04-21
Thank you very much.

---

### Post by Gandalf on 2005-05-01
have a problem couldn't figure out why i get this :o
/etc/apache2/conf.d/alias file:
```

Alias /mydownloads /home/wael/MyDownloads

<Directory /home/wael/MyDownloads>
DirectoryIndex index.html index.php
Options FollowSymLinks
AllowOverride None
order allow,deny
allow from all
</Directory>

Alias /downloads /fat/Download

<Directory /fat/Download>
DirectoryIndex index.html index.php
Options FollowSymLinks
AllowOverride None
order allow,deny
allow from all
</Directory>

```
give always 403, am i missing something?

---

### Post by speedman on 2005-05-01
[QUOTE=Gandalf]give always 403, am i missing something?[/QUOTE]

A 403 error message means access is forbidden.  In your case it most likely indicates that the www-data user that Apache runs as cannot read the directories you have specified.

You can put your downloads directory outside of your home directory and change the ownership to the www-data user as a workaround.


Regards,

SM

---

### Post by Gandalf on 2005-05-01
[QUOTE=speedman]A 403 error message means access is forbidden.  In your case it most likely indicates that the www-data user that Apache runs as cannot read the directories you have specified.

You can put your downloads directory outside of your home directory and change the ownership to the www-data user as a workaround.


Regards,

SM[/QUOTE]
 well i tried leaving it inside the home directory and chown it to www-data:www-data does that makes a difference???

---

### Post by speedman on 2005-05-01
[QUOTE=Gandalf]well i tried leaving it inside the home directory and chown it to www-data:www-data does that makes a difference???[/QUOTE]

chown -R www-data.www-data directory/


Regards,

SM

---

