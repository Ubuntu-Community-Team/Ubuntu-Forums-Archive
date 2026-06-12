---
title: "Can't install DVDStyler from deb"
date: 2005-06-22
forum: General Help
---

### Post by timelord726 on 2005-06-22
Hi all,

I run into the following problem when trying to install the latest version of DVDStyler from the deb file they provide at their web site.

```
danny@danny-ubuntu:~/Desktop$ sudo dpkg -i dvdstyler_1.4-1_i386.deb 
Selecting previously deselected package dvdstyler.
(Reading database ... 104519 files and directories currently installed.)
Unpacking dvdstyler (from dvdstyler_1.4-1_i386.deb) ...
dpkg: dependency problems prevent configuration of dvdstyler:
 dvdstyler depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 dvdstyler depends on libwxgtk2.4 (>= 2.4.3.1); however:
  Version of libwxgtk2.4 on system is 2.4.2.6ubuntu1.
dpkg: error processing dvdstyler (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dvdstyler
```

What am I doing wrong?

Thanks!

---

### Post by n3X_VI on 2005-06-26
the previous version "dvdstyler_1.31-2_i386.deb" works, if you install the "libwxgtk2.4" package via synaptic

greets, n3X

---

### Post by gil-galad on 2005-06-26
I compiled it myself with gtk2 support.  It works well. 

\\//_

---

### Post by Dkinc on 2005-07-14
[QUOTE=timelord726]Hi all,

I run into the following problem when trying to install the latest version of DVDStyler from the deb file they provide at their web site.

```
danny@danny-ubuntu:~/Desktop$ sudo dpkg -i dvdstyler_1.4-1_i386.deb 
Selecting previously deselected package dvdstyler.
(Reading database ... 104519 files and directories currently installed.)
Unpacking dvdstyler (from dvdstyler_1.4-1_i386.deb) ...
dpkg: dependency problems prevent configuration of dvdstyler:
 dvdstyler depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 dvdstyler depends on libwxgtk2.4 (>= 2.4.3.1); however:
  Version of libwxgtk2.4 on system is 2.4.2.6ubuntu1.
dpkg: error processing dvdstyler (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dvdstyler
```

What am I doing wrong?

Thanks![/QUOTE]
 i too am getting that same error as post #1.

is there another program of equal value or a fix to get around the current issue with the invalid version #'s?  please bare in mind i have just made the switch from windows to linux.  I am testing ubuntu for a community of approx. 50 ppls in an office and dvd menu is something they are interested in seeing that ubuntu can/will do without the aid of other programs such as cxoffice.

on a side note.... wow linux has definately come alooooooooong way and i do hope many more office/ppls convert to the "Truth" heh

---

