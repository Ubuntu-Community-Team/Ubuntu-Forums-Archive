---
title: "Apache2 need urgent help! Please"
date: 2007-11-21
forum: General Help
---

### Post by karunr on 2007-11-21
Hi everyone, 
                       I am an engineering student (computer science - major). We have Java Lab now where we are expected to do some programs in perl and php. As guided by my lecturer, I create the perl programs in **/var/www/cgi-bin**. After reading many installation guides on apache2 (since there was no httpd for ubuntu), I tried running it from **/etc/init.d**. But I get the following error message. Can someone please help me. Its very urgent as we have our lab exams coming up in a 2 weeks. 

********************************************************************************************************
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
********************************************************************************************************

---

### Post by enchance on 2007-11-21
Try this. Open up the apache2.conf file
```
$ sudo gedit /etc/apache2/apache2.conf
```
Insert "ServerName localhost" in the next line below "ServerRoot /etc/apache2" that takes care of your server name. Restart apache2 again and see what happens.
```
$ sudo /etc/init.d/apache2 restart
```

---

### Post by az on 2007-11-21
> **karunr said:**
> Hi everyone, 
                       I am an engineering student (computer science - major). We have Java Lab now where we are expected to do some programs in perl and php. As guided by my lecturer, I create the perl programs in **/var/www/cgi-bin**. After reading many installation guides on apache2 (since there was no httpd for ubuntu), I tried running it from **/etc/init.d**. But I get the following error message. Can someone please help me. Its very urgent as we have our lab exams coming up in a 2 weeks. 

********************************************************************************************************
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
********************************************************************************************************

The first line of the message is benign.

The other part of the error is telling you that apache cannot use port 80 - probably because something else (like another instance of apache) is using that port already.

---

### Post by karunr on 2007-11-21
Hi...
I tried it...when I try to restart using the command specified by you, I get the following error message...
********************************************************************************************************
 * Forcing reload of web server (apache2)...                                    
httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
*********************************************************************************************************

I even tried "ps ax | grep apache" (thinking that apache is running)
I get the following message when I do that:

[B]5545 ?        Ss     0:00 /usr/sbin/apache
 5552 ?        S      0:00 /usr/sbin/apache
 5553 ?        S      0:00 /usr/sbin/apache
 5554 ?        S      0:00 /usr/sbin/apache
 5555 ?        S      0:00 /usr/sbin/apache
 5556 ?        S      0:00 /usr/sbin/apache
 6373 pts/0    R+     0:00 grep apache

[/B]

Is apache running instead of apache2? Are they different? If so, where do I put my perl and php programs? 

Thank you

---

### Post by az on 2007-11-21
You need to remove the apache packages and only keep the apache2 ones.


dpkg -l|grep apache

that will list all apache and apache2 packages you currently have installed.  Then, restart apache2.  If you are still having trouble with scripts, make sure you have the appropriate apache2 modules installed.  You may have inadvertently installed apache while trying to install apache2 modules.

---

### Post by karunr on 2007-11-21
I got apache2 running by changing "Listen 80" to "Listen 78". Then I realized that "apache" was running and it was listening to port 80 which caused apache2 to have no ports to listen to. 

Even after that, when I tried to access **"http://localhost:78/"** through my browser, I just got the Index Of/ stuff. It had the directory listing of **/var/www**. I am able to access all directories in that except "cgi-bin". There is also one perl program in that directory. The exact content is as shown below (for http://localhost:78"

[B]Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	21-Nov-2004 01:46 	-
[DIR]	cgi-bin/	22-Nov-2007 00:15 	-
[TXT]	harsha1a.pl	21-Nov-2007 11:16 	1.4K
[DIR]	html/	21-Nov-2007 12:46 	-
[ ]	test.php	21-Nov-2007 23:56 	19
Apache/2.2.3 (Ubuntu) mod_jk/1.2.18 mod_python/3.2.10 Python/2.5.1 PHP/5.2.1 mod_perl/2.0.2 Perl/v5.8.8 Server at localhost Port 78
[/B]

Even when I click on that "harsha1a.pl", another window pops up wherein I have to choose between opening the file with some application and saving the file to disk. 

Can you please help me.

---

