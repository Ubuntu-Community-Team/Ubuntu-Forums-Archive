---
title: "LAMP trouble"
date: 2007-03-16
forum: General Help
---

### Post by M$LOL on 2007-03-16
I installed lamp, and now I get 
```
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/uploader/hi.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```
when trying to view a php file in Firefox. I suppose it has something to do with permissions, but I'm not sure what to do. Help anyone?

---

### Post by Scunizi on 2007-03-16
You might want to try reposting this in the Server Security section.

---

### Post by scxtt on 2007-03-16
is "hi.php" a file you created? (i imagine so) ... what are the permissions on it { **ls -l /var/www/hi.php** }?

are you accessing it via: [http://localhost/hi.php](http://localhost/hi.php) ... ?

---

### Post by llamakc on 2007-03-16
Is php-pear installed? The libapache2-mod-php4 package installed yet?

---

### Post by M$LOL on 2007-03-17
> **scxtt said:**
> is "hi.php" a file you created? (i imagine so) ... what are the permissions on it { **ls -l /var/www/hi.php** }?

are you accessing it via: [http://localhost/hi.php](http://localhost/hi.php) ... ?
Yes, I created it, but I'm accessing it via [http://localhost/uploader/hi.php](http://localhost/uploader/hi.php)

[COLOR="Red"]ciaran@ubuntu:~$ ls -l /var/www/uploader/hi.php
-rw------- 1 ciaran ciaran 22 2007-03-16 16:49 /var/www/uploader/hi.php
ciaran@ubuntu:~$ [/COLOR]

@llamakc:
I'm not sure. How do I check that?

EDIT: I created a html file and I get:
[COLOR="Red"]Forbidden

You don't have permission to access /uploader/hi.html on this server.
Apache/2.0.55 (Ubuntu) PHP/5.1.6 Server at localhost Port 80[/COLOR]

---

### Post by llamakc on 2007-03-17
You need to add read permissions for groups and others.

Those are Ubuntu packages. Use whatever package management system you are comfortable (Synaptic, Adept, Aptitude, dpkg) with to see f they are installed.

---

### Post by M$LOL on 2007-03-17
I have it working now after changing the permissions. I don't have either php-pear or libapache2-mod-php4 installed, but I do have libapache2-mod-php5. Do I need the other two?

---

### Post by llamakc on 2007-03-17
Is it working? That will answer your question. Apparently you do not need them if it is working.

---

### Post by scxtt on 2007-03-17
[COLOR=black]> ciaran@ubuntu:~$ ls -l /var/www/uploader/hi.php[/COLOR]> 
[COLOR=black]-rw------- 1 ciaran ciaran 22 2007-03-16 16:49 /var/www/uploader/hi.php[/COLOR][COLOR=black]any file you want to be server up via apache either needs to be owned by the user defined in apache2.conf (www-data for ubuntu, generally) or readable by "other" ... so, the following 2 will work:[/COLOR]

[COLOR=black]ciaran@ubuntu:~$ ls -l /var/www/uploader/hi.php[/COLOR]
[COLOR=black]-rw----r-- 1 ciaran ciaran 22 2007-03-16 16:49 /var/www/uploader/hi.php[/COLOR]

[COLOR=black]ciaran@ubuntu:~$ ls -l /var/www/uploader/hi.php[/COLOR]
[COLOR=black]-rw------- 1 www-data www-data 22 2007-03-16 16:49 /var/www/uploader/hi.php[/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]think of apache as a little daemon that "grabs" your pages and sends them to the requesting browser - "he" can't access/touch/grab files that "he's" not allowed to --- so you have to help "him" out :)[/COLOR]

---

### Post by M$LOL on 2007-03-18
Yeah it's working. Just out of curiosity, what do they do?

@ scxxt: Thanks for the info.

---

