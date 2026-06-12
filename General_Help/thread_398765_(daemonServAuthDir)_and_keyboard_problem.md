---
title: "(daemon/ServAuthDir) and keyboard problem"
date: 2007-04-01
forum: General Help
---

### Post by bjdekruif on 2007-04-01
Hello all, 

I have been running Ubuntu for some months now, and all works like a charm. 
However, I now have the weirdest problem.

Wednesday I turned off my computer after some work. I didn't play around with the settings or something like that, but the day after, the computer wouldn't start. Before the X server start, I get the message: 

Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but this
does not exist. Please correct gdm configuration /etc/X11/gdm/gdm.conf and re-
start again

The evil part is that even if I start in recovery mode, I cannot use my keyboard. So I got my blinking prompt, while I cannot type. However, I _can_ select that I want to go in recovery mode, so the keyboard is working. 
If I boot in an old kernel, I can type, but my Nvidia driver is compiled for my new kernel, so just using the old kernel won't do.

The directory /var/lib/gdm does exist, and the permissions are rwxrwxr-T. Changing these didn;t do any good.

Does anyone know this problem, and even better, does anyone know a solution to this problem?

Thanks for your time 

bas

---

### Post by bjdekruif on 2007-04-13
Hey all, 

It took me some time, but I solved the problem. 

In the session before this error occurred, I tried to insert the eth1394 module in the kernel, but before I issued the correct command 'modprobe eth1394', I used the wrong command 'depmod eth1394'  I know, a very stupid mistake. 

The result was that the modules.dep was completely wrong, and the XFS module could not be loaded. As a result, my drive was not mounted, which mounted on /var/lib. So gdm starts complaining that the dir /var/lib/gdm did not exist. 

The solution was too easy, but I didn't know (then):

depmod -a

Yours

bas

---

