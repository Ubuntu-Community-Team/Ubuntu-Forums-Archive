---
title: "gedit is not opening as root user"
date: 2012-11-18
forum: General Help
---

### Post by praveenpj on 2012-11-18
praveen@milos:~$ sudo gedit /etc/apt/apt.conf
[sudo] password for praveen: 

** (gedit:4331): WARNING **: Command line `dbus-launch --autolaunch=32635d81c49028f93a9356cb00000008 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
Cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

---

### Post by pkadeel on 2012-11-18
use
```
gksu gedit /path/to/file
```

---

### Post by Wim Sturkenboom on 2012-11-18
I would say
```

gksudo gedit /path/to/file

```

---

### Post by snowpine on 2012-11-18
I recommend:

```
sudo nano /etc/apt/apt.conf
```

or

```
sudo vi /etc/apt/apt.conf
```

---

### Post by vasa1 on 2012-11-18
Recommending vi or nano is all well and good ;) but what makes me concerned is why OP wants to edit /etc/apt/apt.conf in the first place. I've been using Ubuntu for a little over a year and haven't had the need to do so.

---

### Post by Morbius1 on 2012-11-18
Just so we all don't get into a fight over this, gksu and gksudo are the same thing in debian:
> ls -l /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 Apr 30  2012 /usr/bin/gksudo -> gksu

---

### Post by Wim Sturkenboom on 2012-11-19
According to the manpage, that implies that su and sudo are the same :)

But thanks for clearing that up for me; never new that.

---

### Post by dcstar on 2012-11-19
> **vasa1 said:**
> Recommending vi or nano is all well and good ;) but what makes me concerned is **why OP wants to edit /etc/apt/apt.conf in the first place.** I've been using Ubuntu for a little over a year and haven't had the need to do so.

Probably because another misguided "HOWTO" somewhere just lists commands that people blindly follow. The interesting thing about the people who continually follow these things is that their systems invariably develop all sorts of strange problems that never EVER seem seem to occur in systems that people treat correctly.

They then come to places like this asking for help with now non-standard systems that can be so fundamentally broken that a total reinstall is the only solution (keep reading the posts in this forum if you have any doubts.....).

Funny world, innit?

---

### Post by dcstar on 2012-11-19
> **Morbius1 said:**
> Just so we all don't get into a fight over this, gksu and gksudo are the same thing in debian:

Arrggghhhh!

su and sudo **are different**! gksu and gksudo **are different** for the exact same reason - they are run in different User environments:

*"Su switches you to the root user account and requires the root account’s password. Sudo runs a single command with root privileges – it doesn’t switch to the root user or require a separate root user password."*

[http://www.howtogeek.com/111479/htg-explains-whats-the-difference-between-sudo-su/](http://www.howtogeek.com/111479/htg-explains-whats-the-difference-between-sudo-su/)

---

### Post by stinkeye on 2012-11-19
> **dcstar said:**
> Arrggghhhh!

su and sudo **are different**! gksu and gksudo **are different** for the exact same reason - they are run in different User environments:

*"Su switches you to the root user account and requires the root account’s password. Sudo runs a single command with root privileges – it doesn’t switch to the root user or require a separate root user password."*

[http://www.howtogeek.com/111479/htg-explains-whats-the-difference-between-sudo-su/](http://www.howtogeek.com/111479/htg-explains-whats-the-difference-between-sudo-su/)
In my quantal install /usr/bin/**gksudo** links to /usr/bin/**gksu**.

---

### Post by Grenage on 2012-11-19
> **stinkeye said:**
> In my quantal install /usr/bin/**gksudo** links to /usr/bin/**gksu**.

Indeed; **sudo** and **su** are different things, but afaik, **gksu** and **gksudo** are not.

Edit: I assume this is because it's fine to use **su** for graphical apps, if you do in fact want to run the apps and config files as root.

---

### Post by Abhinav Kumar on 2012-11-19
> **vasa1 said:**
> Recommending vi or nano is all well and good ;) but what makes me concerned is **why OP wants to edit /etc/apt/apt.conf **in the first place. I've been using Ubuntu for a little over a year and haven't had the need to do so.
Hi vasa1,
Sorry to interrupt you despite being a new user (as compared to you who has a lot of experience of using linux ):smile:

Sometimes people need to access the network through the proxy server. If the proxy requires a username and a password, you need to manually edit the /etc/apt/apt.conf file and write your username and password so that softwares can be installed and even ubuntu can be upgraded through the proxy.  

Regards,
Abhinav

---

