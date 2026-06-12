---
title: "How to manage services in 12.04 desktop"
date: 2012-10-27
forum: General Help
---

### Post by TexasGaidheal on 2012-10-27
I have installed the  Ubuntu 12.04 desktop version, but what I really need is a server with a graphical user interface. I have installed the additional Gnome packages so that I can use the older Gnome gnome desktop as well as Unity, but some things which I had in other Linux distributions are missing, and I do not know how to replace them with something equivalent on Ubuntu.

In particular, I need to be able to manage services. I have installed HylaFAX, Apache, and MySQL and will be installing other server-type software packages as well.

I need to be able to manage these. In Fedora, I had a graphical management tool that would let me start, stop, and restart services, see which services were running, select which would start automatically when the OS booted, and so forth. Is there something that will do this for me in Ubuntu Desktop 12.04?

---

### Post by btindie on 2012-10-27
See this [thread]("http://ubuntuforums.org/showthread.php?t=1524899&page=2") about a gui.

It's easy enough to do it through the command line. Take a look at the following links:

[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)
[http://www.linuxplanet.com/linuxplanet/tutorials/7033/1](http://www.linuxplanet.com/linuxplanet/tutorials/7033/1)

TIP: to disable an upstart job from starting automatically at boot you need to comment out the "start on" line in the job file. So to disable mysql, type "sudoedit /etc/init/mysql.conf" and put a hash '#' in front of "start on "....

---

