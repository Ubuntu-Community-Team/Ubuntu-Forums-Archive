---
title: "XINE to play DVD's"
date: 2005-05-18
forum: General Help
---

### Post by snairofilac on 2005-05-18
want to watch DVD in XINE.  

i have libdvd* installed.  upon insert of DVD, xine shows the opening bluescreen FBI warning, then won't proceed to menu.  gives error:

The source can't be read.

Maybe you don't have enough rights for this, or source doesn't contain data (eg not disc in drive)(Error Reading from DVD)

any suggestions?

---

### Post by snairofilac on 2005-05-18
debug

siddhartha@ip70-186-115-166:~$ sudo apt-get install libdvdcss2
Password:
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
siddhartha@ip70-186-115-166:~$

---

### Post by estel on 2005-05-19
Did you add Milarat as a repository?

---

### Post by jobezone on 2005-05-19
[QUOTE=estel]Did you add Milarat as a repository?[/QUOTE]
 Backports reporitories also have libdvdcss2 . I recomend you to use the backports, since these are maintained specifically for Ubuntu, while Marillat is maintaned for Debian, which works, but doesn't care you're using ubuntu.

---

### Post by snairofilac on 2005-05-20
adding backports via 

[http://ww.ubuntuguide.org](http://ww.ubuntuguide.org)

searching libdvd and installing did the trick thanx for help!!

---

