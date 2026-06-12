---
title: "Gnome-System-Monitor &amp; &quot;SELinux was found but is not enabled&quot;"
date: 2007-12-04
forum: General Help
---

### Post by FrankQuist on 2007-12-04
Hi, 

Since today I have been unable to run Gnome-System-Monitor. It gives the following error: "SELinux was found but is not enabled". This sounds kind of worrying to me, since it was working fine before, and SELinux is a security thing and all... Does anybody have any tips on how to remedy this, and what the security risk is?

Thanks in advance.

Some details:
I'm on Gutsy, using 32-bit. 
Uname -a: "Linux Prometheus 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux". libselinux1 and libselinux1-dev are installed. No big system tweaks... installed Gnome-DO from a PPA, and VirtualBox from an external archive, have partner repo enabled. No backports or anything. Have a couple installed .debs. New Opera beta.

EDIT: Oh, and this only seems to happen at certain times. I have a Dell computer with specs that I forgot and which are conveniently located in the system applet I cannot start.

---

### Post by Gambini on 2007-12-04
I seem to get that error as well when trying to run it in fluxbox, but it still shows up about 90% of the time. The other 10%, I just restart (ctrl+alt+backspace) and it will work again. That's hopefully a temporary band-aid until I figure out what is actually giong on or someone else does.

---

### Post by FrankQuist on 2008-01-08
I've posted the bug at [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087). If your experience matches mine, elaboration is welcome.

---

### Post by whoscheesemine on 2008-03-06
Here is another thread I've posted about this issue that anyone can feel free to follow if nothing comes out of this one.

[http://ubuntuforums.org/showthread.php?p=4467286#post4467286](http://ubuntuforums.org/showthread.php?p=4467286#post4467286)

---

### Post by Magnentius on 2008-05-08
I received this error message from gnome-system-monitor too. So I searched for answers and I found via [wikipedia]("http://en.wikipedia.org/wiki/Selinux") this [site]("http://lwn.net/Articles/273992/") which states that SELinux is not enabled in Ubuntu 8.04 by default. So the error message in gnome-system-monitor isn't an error message at all. To resolve the problem you'll have to install the SELinux package from synaptic or simply type at the konsole:

> sudo apt-get install selinux

I wonder why the hell selinux isn't enabled by default.

---

### Post by BBirdtree on 2008-06-29
> **Magnentius said:**
> I received this error message from gnome-system-monitor too. So I searched for answers and I found via [wikipedia]("http://en.wikipedia.org/wiki/Selinux") this [site]("http://lwn.net/Articles/273992/") which states that SELinux is not enabled in Ubuntu 8.04 by default. So the error message in gnome-system-monitor isn't an error message at all. To resolve the problem you'll have to install the SELinux package from synaptic or simply type at the konsole:



I wonder why the hell selinux isn't enabled by default.
to me apt-get told me to install checkpolicy instead.

---

