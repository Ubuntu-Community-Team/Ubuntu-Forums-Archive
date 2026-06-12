---
title: "Installing KDE on Ubuntu"
date: 2007-04-26
forum: General Help
---

### Post by Graham1 on 2007-04-26
Hi

This might sound like a daft question, but... is it possible to install KDE on Ubuntu 7.04? I do have an ISO for Kubuntu but just wondered if the two windows manager could run together on the same setup.

:)

---

### Post by Cable on 2007-04-26
Read [this]("http://www.psychocats.net/ubuntu/kde").

---

### Post by steevk on 2007-04-26
> Please note that some people may tell you to install KDE using Synaptic Package Manager or apt-get.

Use aptitude instead, because it'll make KDE easier to remove later if you wish to do so. 

Why is this?

---

### Post by dreadlord_chris on 2007-04-26
> **steevk said:**
> Why is this?

Actually, that's not really true anymore. Apt-get has gotten **far** more intelligent of late:
> 
This APT has Super Cow Powers.


---

### Post by unnes on 2007-04-26
> **Cable said:**
> Read [this]("http://www.psychocats.net/ubuntu/kde").

This made installing KDE a cinch. Now I wonder why I used GNOME for so long!

---

### Post by Cable on 2007-04-26
Glad I could help!  :-)  If you're wondering why aptitude is suggested over apt-get, read [this]("http://www.psychocats.net/ubuntu/aptitude").
Also, if you install KDE and end up wanting to remove it later, read [this]("http://www.psychocats.net/ubuntu/puregnome").  If you end up liking KDE and wanting to get rid of GNOME, read [this]("http://www.psychocats.net/ubuntu/purekde").
On second thought, just bookmark [this]("http://www.psychocats.net/ubuntu/index") site!  :-P  Explore it.  It's a great guide site that aysiu created.  I find myself pointing people to it all the time.  Share the knowledge!

> **dreadlord_chris said:**
> Actually, that's not really true anymore. Apt-get has gotten **far** more intelligent of late:
While Apt-get may have gotten better, it still does not seem to handle dependencies as well as aptitude.  I always use aptitude to install things just in case I ever want to remove them along with all of their dependencies.  It just saves time that would otherwise be wasted by trying to track down what other stuff was installed along with the program I just removed.

---

### Post by dreadlord_chris on 2007-04-28
> **Cable said:**
> While Apt-get may have gotten better, it still does not seem to handle dependencies as well as aptitude.  I always use aptitude to install things just in case I ever want to remove them along with all of their dependencies.  It just saves time that would otherwise be wasted by trying to track down what other stuff was installed along with the program I just removed.

Actually, aysiu has changed his stance on that:
[http://ubuntuforums.org/showthread.php?t=424797](http://ubuntuforums.org/showthread.php?t=424797)
> **aysiu said:**
> 
Well, until Edgy and Feisty--now apt-get has autoremove, which gets rid of unused dependencies.


---

