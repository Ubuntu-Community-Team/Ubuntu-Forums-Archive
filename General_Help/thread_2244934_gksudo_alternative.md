---
title: "gksudo alternative?"
date: 2014-09-19
forum: General Help
---

### Post by redrumrogue on 2014-09-19
Hi folks,

When I first installed ubuntu 14.04 a while back I discovered that gksudo (gksu) is not included in ubuntu anymore.  Does anybody know why?  What should we use instead to run GUI apps as root?  I read somewhere that "sudo -i" does the same thing, and I've been using that without any problems so far, but I don't know for certain if it's the same as gksudo.

Any advice would be appreciated.

---

### Post by slickymaster on 2014-09-19
Here's a good explanation on it: [Why is gksu no longer installed by default]("http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default")

---

### Post by redrumrogue on 2014-09-19
Ok that's interesting.  So we should forget about gksudo based on that.  That thread doesn't really make it clear what is the best alternative though.  Slicky, do you use sudo -i?

---

### Post by slickymaster on 2014-09-19
The intended alternative is supposed to be pkexec.

In my laptop I still have **gksu** installed, so I'll keep on using it. But I have a few VMs boxes, mainly for ISO and packages testing, where I use **sudo -i**.

Xubuntu, from Utopic onward, and to allow users to use pkexec for selected applications instead of gksu(do), will ship appropriate policy files for Thunar and Mousepad and being a Xubuntu guy myself if having to change I'll probably change to pkexec.

---

### Post by grahammechanical on 2014-09-19
As far as I know, there is not an alternative to gksu but there is a different way of doing things. Some of us found out that gksu was not installed by default when we were testing 14.04 during its development period. Have a look through this thread

[http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)

To use pkexec we create policies for the programs that we want to run with root/administrator privileges. Then when we run pkexec <program> we get asked to authenticate by entering our administrator password. It is the PolicyKit policies that force certain utilities to ask for authentication when the utility is loaded.

It would be nice if Ubuntu came with policies for Gedit and Nautilus by default but that has not yet happened. Maybe in the future.

Regards.

P.S. in that thread it is suggested to use sudo -H. Ignore the error messages in the terminal. That is also discussed in that thread.

---

### Post by ibjsb4 on 2014-09-19
I just went ahead and installed gksu so I could use gksudo.  Also when pkexec will not work in a launcher (as happen more than once to me), it makes it easy to repair by replacing pkexec with gksudo.

---

