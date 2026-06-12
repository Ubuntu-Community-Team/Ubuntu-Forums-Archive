---
title: "Ubuntu Server Edition problem, please read, I can't install PHP!"
date: 2007-09-26
forum: General Help
---

### Post by easytec on 2007-09-26
Well, I installed Ubuntu Server Edition, using [this]("http://ubuntuforums.org/showthread.php?t=223805") post. It helped ideally.
Thus, allowing me to be able to use the GNOME desktop.
But I noticed, although I asked it to install LAMP as well, as it is, it is a Linux Kernel Ubuntu Server Edition running LAMP!
I managed to install Apache via Webmin, MySQL, also ProFTPD and Squid, BIND, etc.
But now I need to have PHP, Python and Pearl connected to and attached to Apache.
This for each using the Linux Shell in the GNOME desktop.
```
sudo app-start install <module>
```
Sudo ('substitute user do', I also found out that sudo actually meant 'substitute user do <command>' from 'substitute user' <command>).
After doing so, I got Apache working.
Is there a way of installing all of lamp?
I need the PHP/Python/Pearl package and instructions of how to plug it in.
Thanks. :)

---

### Post by reckless2k2 on 2007-09-26
can't you install this via webmin? i remember being able to install things via webmin in the modules area i think. anyway....

google: the perfect setup ubuntu 7.04

---

### Post by easytec on 2007-09-27
No, it appears not.
It just installs Apache 2.0.
At the moment, oh wait...
I think this works:
```
sudo apt-get install php5
```
This way works good:
```
sudo apt-get install <likely module name>
```
I just use Konsole.

---

### Post by easytec on 2007-09-27
Anyone know how to change the document path from /var/www/ in Apache to /home/easytec/Desktop/SYSTEM/?

---

### Post by easytec on 2007-09-27
Found it, DOCUMENT OPTIONS.

---

