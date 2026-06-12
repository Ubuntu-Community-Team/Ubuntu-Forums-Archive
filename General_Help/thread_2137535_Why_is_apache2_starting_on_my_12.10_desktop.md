---
title: "Why is apache2 starting on my 12.10 desktop?"
date: 2013-04-21
forum: General Help
---

### Post by coldraven on 2013-04-21
This is 12.10 running on a laptop with all the latest updates.
Since getting the latest kernel update I get to see some messages when booting. The ones that end in [OK] that precede the splashscreen.
I also get a very rough initialisation of the video card, a white screen with black "noise" for a split second.
I have noticed that apache2 is being started. I have searched the system logs but not found anything.
The "top" command does not show it.
I get the following from "ps" but how do I find what starts it?

```
coldraven@happy:~$ ps ax | grep apache2
 1172 ?        Ss     0:00 /usr/sbin/apache2 -k start
 1174 ?        S      0:00 /usr/sbin/apache2 -k start
 1175 ?        Sl     0:00 /usr/sbin/apache2 -k start
 1176 ?        Sl     0:00 /usr/sbin/apache2 -k start
25811 pts/0    S+     0:00 grep --color=auto apache2


```

Thanks

---

### Post by 3rdalbum on 2013-04-21
> **coldraven said:**
> This is 12.10 running on a laptop with all the latest updates.
Since getting the latest kernel update I get to see some messages when booting. The ones that end in [OK] that precede the splashscreen.
I also get a very rough initialisation of the video card, a white screen with black "noise" for a split second.
I have noticed that apache2 is being started. I have searched the system logs but not found anything.
The "top" command does not show it.
I get the following from "ps" but how do I find what starts it?

```
coldraven@happy:~$ ps ax | grep apache2
 1172 ?        Ss     0:00 /usr/sbin/apache2 -k start
 1174 ?        S      0:00 /usr/sbin/apache2 -k start
 1175 ?        Sl     0:00 /usr/sbin/apache2 -k start
 1176 ?        Sl     0:00 /usr/sbin/apache2 -k start
25811 pts/0    S+     0:00 grep --color=auto apache2


```

Thanks

The easiest way to find out would be to try removing Apache2. When asking for confirmation that you really want to remove Apache, it will list any packages on your system that depend on Apache2 and would also need to be removed. Of course, once you know, you can hit N to cancel the removal of Apache.

---

### Post by rnerwein on 2013-04-21
hi
looks like upstart.
--> cd /etc/init and: grep apache *
     there i guess you will see where apache is started. if you ain't want to start apache --> comment it out.
oh - have a look in rc.local too.
ciao

---

### Post by coldraven on 2013-04-21
> The easiest way to find out would be to try removing Apache2. When  asking for confirmation that you really want to remove Apache, it will  list any packages on your system that depend on Apache2 and would also  need to be removed. Of course, once you know, you can hit N to cancel  the removal of Apache.

I used Synaptic and there were no dependencies, only apache2 was going to be removed.


> looks like upstart.
--> cd /etc/init and: grep apache *
     there i guess you will see where apache is started. if you ain't want to start apache --> comment it out.
oh - have a look in rc.local too.

Nothing in /etc/init/upstart* or /etc/rc.local

Next suggestion?  :)

---

### Post by Iowan on 2013-04-21
**ps -ef** should reveal parent PID.

---

### Post by coldraven on 2013-04-22
> **Iowan said:**
> **ps -ef** should reveal parent PID.

That gives the following but I don't know what it means :(
```

    root      1176     1  0 06:57 ?          00:00:00 /usr/sbin/apache2 -k start
www-data  1181  1176  0 06:57 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1183  1176  0 06:57 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1184  1176  0 06:57 ?        00:00:00 /usr/sbin/apache2 -k start


```

In /var/www/ there is the usual "It Works!" index.html
In /var/www/dwww I found an index page for Debian Documentation, I don't remember installing this.

```
/var/www/dwww$ ls
debian.png  dwww.css  index.html  man  menu


```

I am not too alarmed, I will be doing a fresh install of 13.04 when it is released shortly. I think I will be dual booting with CentOS as I need to learn the RHEL way of doing things.
Thanks for the responses, I'll mark this as solved shortly.

---

### Post by mastablasta on 2013-04-22
> **coldraven said:**
> In /var/www/dwww I found an index page for Debian Documentation, I don't remember installing this.




perhaps one of the programmes pulled it in as dependecy. hard to say since we do not know what and how you were installing.

---

### Post by coldraven on 2013-04-22
> **mastablasta said:**
> perhaps one of the programmes pulled it in as dependecy. hard to say since we do not know what and how you were installing.

You are probably right although it could have been there all the time.
When I install 13.04 I will check to see if I have a /var/www directory.
Meanwhile, I will mark this a solved.Thanks for your input.

---

