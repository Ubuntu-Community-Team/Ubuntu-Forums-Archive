---
title: "Apache+PHP Nightmare"
date: 2008-06-29
forum: General Help
---

### Post by shawnrgr on 2008-06-29
I've searched the net for an hour and a half now. I'm turning to you guys for help...

Sounds simple, XAMPP. I've installed this without issue on a windows box. But windows doesn't have the permissions system linux does. So when I installed it on my Ubuntu box i wasn't able to access anything on local host but what came with xampp. 403 forbidden errors.. lots of them.

Yes I searched the net to fix this. Nothing seemed to work, nothing seemed to be worded for a simpleton like myself. I gave up after an hour...

So i found a lamp how to and decided to give it a go.

Now I have apache running however localhost still points to localhost/xampp and i don't know how to change that. its still working though... localhost/test.html ran without issue.

So i continued the steps for php...

installed find restarted apache and got this...

```
sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

but it was still working for html and read that its not an issue if im not setting this up for all on a network so i continued and decided to test the php..

guess yet?

yea no go. firefox wants to download the php file because it doesn't know what to do with it.

I need so help guys... Anything would be nice.

---

### Post by shawnrgr on 2008-06-30
Shameless *bump* :(

---

### Post by cpetercarter on 2008-06-30
If you haven't already done so, have a look at [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP"). The section on virtual hosts may help in changing where "localhost" points to.

There is also a section on "troubleshooting" (immediately following "installing php 5") which deals with the problem of firefox wanting to download the php script.

---

### Post by hyper_ch on 2008-06-30
[http://www.howtoforge.com](http://www.howtoforge.com) --> there are perfect howtos that you can follow to setup a complete webserver.

---

### Post by shawnrgr on 2008-06-30
> **cpetercarter said:**
> If you haven't already done so, have a look at [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP"). The section on virtual hosts may help in changing where "localhost" points to.

There is also a section on "troubleshooting" (immediately following "installing php 5") which deals with the problem of firefox wanting to download the php script.

I don't know what I would do without you guys... seriously :) Worked like a charm. No more testing my sites on an actual godaddy server ;)

Should I be worried about security?

---

### Post by cpetercarter on 2008-06-30
I do not think you need to worry that your apache etc installation will cause security risks, unless you have set up your firewall so as to permit connections from other computers. (Firestarter > Policy > Inbound Traffic Policy will tell you whether you have set up any such permissions. By default, there are none.)

---

### Post by fragos on 2008-06-30
With LAMP (Apache2, MySQL & PHP) installed you still need to tell Apache2 that it can run PHP. /etc/apache2/httpd.conf is probably empty and need to have the following three lines added:

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

### Post by hyper_ch on 2008-07-01
better to use
```

sudo a2enmod php5 && sudo /etc/init.d/apache restart

```
than adding those manually

---

