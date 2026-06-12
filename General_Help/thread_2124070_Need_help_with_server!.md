---
title: "Need help with server!"
date: 2013-03-09
forum: General Help
---

### Post by caleb12134 on 2013-03-09
Hi i am a minecraft server host. and we just got a machine with ubuntu. we want to know how to access all folders even if we arent the "owners" of the file. EX we installed Multicraft panel and we cant even access the files. And the FTP wont work?

---

### Post by agillator on 2013-03-10
First, you need to understand Linux permissions. See [https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions) for an explanation. In order to do something with a file for which permission is denied, then, you would need to access it as root. That is what sudo does for you, if you have permission to use sudo. For information on sudo, check the man page (man sudo in a terminal window). Note Ubuntu does NOT activate a root account for security reasons. Sudo is normally adequate to perform root functions.

---

### Post by caleb12134 on 2013-03-10
can you explain step by step on how i change permissions of my apache web folder on ubuntu desktop?

---

### Post by agillator on 2013-03-10
As I said earlier, the first step is to understand the permission system. Without understanding that, changing permissions is actually counterproductive and may create major, fatal problems. Basically as either root or the owner of a file you use the chmod command to set the new set of permissions. Since I know nothing about your program, minecraft, I really can't tell you what the permissions need to be. But here is a link that may address the situation you are asking about: [http://serverfault.com/questions/130897/permission-settings-for-apache2-web-content-directories-with-several-users](http://serverfault.com/questions/130897/permission-settings-for-apache2-web-content-directories-with-several-users). I get the impression you know little or nothing about Ubuntu or Linux. We have all been there at one time or another and that is not a problem. However, I also get the impression, I hope in error, that you really really don't want to learn how to use them but just want someone to give you a cookbook recipe. That is something few here will do. We will do much to help but will not do it for you. Give a man a fish, etc. If I am wrong, I certainly apologize. If you have investigated the permission system, sudo and chmod and are still having difficulty then please do ask again and be very specific about what is happening, what you have tried that hasn't worked, what you don't understand.

---

### Post by caleb12134 on 2013-03-14
I actually want to learn. I am having trouble configuring PHPmyadmin?? I installed it and it wont work??I tried 192.168.1.3/phpmyadmin and it didnt work?? I then looked in /www and there was only the index.html and the multicraft folder??? Please help. I have googled my brain to death? :)

---

### Post by steeldriver on 2013-03-14
AFAIK the default install of phpmyadmin doesn't put anything in /var/www - I have a little 'play' server which only has the default index.html i.e.

```
$ ls -l /var/www
total 4
-rw-r--r-- 1 root root 177 Jan 30 18:26 index.html
```

Have you checked that your basic php setup is working correctly? e.g. create an minimal php file that just runs phpinfo and point your browser at that?

```

$ cat /var/www/phpinfo.php
<?
phpinfo();
?>

```

---

### Post by agillator on 2013-03-14
We are going to have to get into the configuration files, it would appear. So, we need to know how apache was installed. Look in the directory /etc/apache2 and see if there is a file apache2.conf among others and directories conf.d and mods-enabled among others. If so, then that tells us how apache was installed. Look in the mods-enabled directory and see if php5.conf and php5.load are there. Then look in the conf.d directory and see if phpmyadmin.conf is there.

---

