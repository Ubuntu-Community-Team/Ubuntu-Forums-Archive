---
title: "Printer skipping every alternate job"
date: 2012-10-23
forum: General Help
---

### Post by varunmehta on 2012-10-23
I've installed the new Canon Selphy 900, using the Selphy 520 drivers (these are are the most stable ones available).

The problem I have is every alternate print is skipped, and some times the second job is printed before the first one, and the first is never printed! 

I gave the command (from page_log)
```
Canon-CP900 photobooth 3 [22/Oct/2012:23:30:54 -0400] 1 1 - localhost lion.jpg - -
Canon-CP900 photobooth 4 [22/Oct/2012:23:31:14 -0400] 1 1 - localhost tiger.jpg - -

```

which are two separate files I'm trying to print with a picture of each of the creatures. The printer, just printed tiger.jpg and stopped as if it had only on job and no other files. 

I've attached the printer debug logs to the post, it's a long file, but I'm totally clueless on what could be causing a problem. This is on a fresh install of lubuntu 12.10.

```
lpstat -o
WARNING: gnome-keyring::  couldn't connect to: /run/user/photobooth/keyring-wnIiP9/pkcs11: No such file or directory
Canon-CP900-5           photobooth           0   Tue 23 Oct 2012 12:06:01 AM EDT
Canon-CP900-6           photobooth           0   Tue 23 Oct 2012 12:06:08 AM EDT

```

On more point the WARNING, always keeps popping up. 

```

sudo ls -l /var/spool/cups/
total 34884
-rw-r----- 1 root lp        0 Oct 23 00:06 00000000
-rw-r----- 1 root lp        0 Oct 23 00:06 00000001
-rw------- 1 root lp      792 Oct 22 23:18 c00001
-rw------- 1 root lp      808 Oct 22 23:18 c00002
-rw------- 1 root lp      854 Oct 22 23:30 c00003
-rw------- 1 root lp      855 Oct 22 23:31 c00004
-rw------- 1 root lp      858 Oct 22 23:31 c00004.O
-rw------- 1 root lp      755 Oct 23 00:11 c00005
-rw------- 1 root lp      739 Oct 23 00:06 c00005.O
-rw------- 1 root lp      755 Oct 23 00:11 c00006
-rw------- 1 root lp      739 Oct 23 00:06 c00006.O
-rw-r----- 1 root lp  8383285 Oct 22 23:18 d00001-001
-rw-r----- 1 root lp 11595570 Oct 22 23:18 d00002-001
-rw-r----- 1 root lp  8383285 Oct 22 23:30 d00003-001
-rw-r----- 1 root lp  7312430 Oct 22 23:30 d00004-001
drwxrwx--T 2 root lp     4096 Oct 15 15:44 tmp

```

Any pointers or help to fix this issue will be very useful. Thank you for your help in advance.

---

### Post by ~LoKe on 2012-10-23
What's the output of:
```
ps ax | grep gnome-key
```

---

### Post by pdc on 2012-10-23
I got immersed in reading your compressed error log

I googled on 

> CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files

and in this thread

[http://ubuntuforums.org/showthread.php?p=11929368](http://ubuntuforums.org/showthread.php?p=11929368)

I wondered if post #2 might have any relevance for you

(Are we to assume you are using the gutenprint driver?)

---

### Post by varunmehta on 2012-10-23
> **~LoKe said:**
> What's the output of:
```
ps ax | grep gnome-key
```

Output from the grep;
```
ps ax | grep gnome-key
 1132 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --start --components=ssh
 2612 pts/0    S+     0:00 grep --color=auto gnome-key
```

---

### Post by varunmehta on 2012-10-23
> **pdc said:**
> (Are we to assume you are using the gutenprint driver?)

I'm using the gutenprint driver, deleting and reinstalling the printer did not help. I ended up rebuilding the system, and still stuck.

---

### Post by varunmehta on 2012-10-24
Bump! Any one ? Still stuck..

---

### Post by varunmehta on 2012-10-24
Found some more info;

While the print job was in progress, I got this error message in the syslog.
```

Oct 24 19:37:24 photobooth kernel: [82850.440782] usblp0: removed

```

Found a bug related to this issue;
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1001028](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1001028) 

Trying to reinstall cups and see if that resolves the issue. Moving down from 12.10 to 12.04. Might go down all the way to 8.04, if this does not work.

---

### Post by pdc on 2012-10-24
> [COLOR="Red"]Bump! Any one ? Still stuck[/COLOR].. 

I think your question/statement sort of assumes that someone out there is holding a secret answer;

....I very much doubt that.......

Canon do not release a driver for this printer; (there are NO linux drivers for this series of printers............)

existing drivers (gutenprint) do not fully work; you tell us that; the maintainers of gutenprint would I am sure be happy to work with you; however you need to contact them directly 

[http://gimp-print.sourceforge.net/p_Contact_Us.php](http://gimp-print.sourceforge.net/p_Contact_Us.php)

let us know how you get along

your post prompted me to investigate this class of printers; a couple of reviews recommended the ip100 

[http://www.canon.com.sg/business/products/printers/inkjet-printers/pixma-ip100](http://www.canon.com.sg/business/products/printers/inkjet-printers/pixma-ip100)

as being the best photo printer

and it comes fully supported with linux packages

for ubuntu, using debian packages.......

for the ip100 there is the [COLOR="SeaGreen"]iP100 series IJ Printer Driver Ver. 3.70 for Linux (debian Packagearchive)[/COLOR]

from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100119002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119002.html)

the driver has an install.sh script

and comes with both 32bit and 64bit packages that would be identified by the install.sh script

so I appreciate you helping us with this

---

