---
title: "Automatix errors"
date: 2006-12-08
forum: General Help
---

### Post by David Valentine on 2006-12-08
Automatix has always worked great for me, including about a couple of weeks ago when I installed Kubuntu 6.10 on my Dell D505.  Because I had some wifi issues, however, I wound up doing another clean Kubuntu install, and then another again.  During these latter installs, however, Automatix has been a bit disappointing.  It successfully installed several packages, but also consistently has failed to install several others:  Sun Java 1.5 JRE, Extra fonts, DVD Ripper, Flash player, MPlayer and FF plugin, Media Players, Multimedia editing, and Acrobat reader.  All except Java fail with > an apt-based error occurred and installation was unsuccessful.  With Java, Automatix thinks the install was successful (it wasn't) even though I was never prompted for the EULA.

Does anyone have any idea what's going on here?

---

### Post by taurus on 2006-12-08
1.  Have you tried to install it again?

2.  What's the output of this command from a terminal then?
```
java -version
```

---

### Post by wpshooter on 2006-12-08
David:

My experiences with Automatix have been the same as yours.

That's why I no longer try to use it.

Good luck.

---

### Post by David Valentine on 2006-12-08
> 1.  Have you tried to install it again?Yes, including after rebooting. > 2.  What's the output of this command from a terminal then?```
$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```One other thing:  when I watch the terminal window Automatix opens, I see that apt is failing to find the various packages I'm trying to install, even though Automatix sources are intact in sources.list and sudo apt-get update yields no errors.

---

### Post by David Valentine on 2006-12-08
When I run Automatix from the command line and it attempts to install Java, here is the error that shows up in the terminal window:  ```
/usr/lib/automatix2/main_interface.py:200: GtkWarning: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed
Traceback (most recent call last):
  File "/home/arnav/resin2/debtree/source/usr/lib/automatix2/main_interface.py", line 352, in start_exec
AttributeError
:
main_ui instance has no attribute 'activity_log'
```And when I try to install Acrobat reader, here is the result```
script1 died fataly: An apt-based error occured and installation was unsuccessful

ERRORS OR WARNINGS WHERE REPORTED
--------------------------------------------------
--------------------------------------------------
1 - An apt-based error occured and installation was unsuccessful

-----------------------------------
Traceback (most recent call last):
  File "/home/arnav/resin2/debtree/source/usr/lib/automatix2/main_interface.py", line 352, in start_exec
AttributeError
:
main_ui instance has no attribute 'activity_log'

```

---

### Post by arnieboy on 2006-12-08
Read post 16 in the following thread:
[http://www.getautomatix.com/forum/index.php?showtopic=538](http://www.getautomatix.com/forum/index.php?showtopic=538)

---

### Post by David Valentine on 2006-12-08
Actually, what was missing from my sources.list were the lines```
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
```What I had was this:```
deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse
```After adding the two lines quoted to my sources.list, all seems to be going OK again.  Thanks!

---

