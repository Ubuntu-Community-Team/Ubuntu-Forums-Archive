---
title: "Error occured"
date: 2008-01-27
forum: General Help
---

### Post by Totallypclost on 2008-01-27
Hi, i keep getting this everytime i go into synaptic, is there away of stopping this? it is getting annoying.

> E: mnogosearch-common: subprocess post-installation script returned error exit status 9

T.I.A.

---

### Post by jan quark on 2008-01-27
it seems that it's a broken dependencies issue 
like here [http://ubuntuforums.org/showthread.php?t=520022](http://ubuntuforums.org/showthread.php?t=520022)
try to follow the instructions of the link above
but I am not na expert myself but will read some more on this issue

do you have installed mnogosearch-common in the recect past?

---

### Post by Totallypclost on 2008-01-27
I've got mnogosearch-common installed, re-installed "debconf" and still get the previous message, even after a reboot it is still there when i do a install of any packages.

The cd is one out of Linux mag, **not** a download.

So i'm not sure whats going on,:confused: being a noob i would have thought it would be easy to sort the deps, which i've checked and D/L'd, is there something i'm missing?

---

### Post by Totallypclost on 2008-01-27
tried the suggestions,just done dpkg and got:-

micheal@micheal-desktop:~$ sudo dpkg --configure -a
[sudo] password for micheal:
Setting up mnogosearch-common (3.2.41-2) ...
Template #1 in /var/lib/dpkg/info/mnogosearch-common.templates does not contain a 'Template:' line
dpkg: error processing mnogosearch-common (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 mnogosearch-common
micheal@micheal-desktop:~$

---

