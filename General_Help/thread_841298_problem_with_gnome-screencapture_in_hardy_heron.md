---
title: "problem with gnome-screencapture in hardy heron"
date: 2008-06-26
forum: General Help
---

### Post by lmsurprenant on 2008-06-26
I am trying to figure out why 'Print Screen' does not work for me since I upgraded to Hardy Heron.  I notice the following from the terminal

:~$ /usr/bin/gnome-screenshot 
Segmentation fault
:~$ sudo /usr/bin/gnome-screenshot 
[sudo] password for lee: 
:~$

So when running as root, I got the popup to save my new screencapture as expected, but otherwise I just get a segfault.  Is this a bug?  I really shouldn't need to be root to take a screenshot, any ideas?  Not sure where to look in terms of changing permissions...

---

### Post by lmsurprenant on 2008-06-30
This is now working properly for me.  Perhaps it was fixed with a recent update or after a reboot...

---

