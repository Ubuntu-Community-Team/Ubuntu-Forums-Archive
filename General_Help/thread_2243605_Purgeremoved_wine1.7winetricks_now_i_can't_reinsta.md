---
title: "Purge/removed wine1.7/winetricks now i can't reinstall wine. dpkg"
date: 2014-09-10
forum: General Help
---

### Post by bobbyallan on 2014-09-10
I get a dpkg error

Sub-process /usr/bin/dpkg returned an error code (1)
~~~~~~~~~~~~~~~~~~~
"in ubuntu software center"
error while attempting to install.

thanks in advance for any help. ;)


```


installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 270098 files and directories currently installed.)
Preparing to unpack .../wine1.6_1%3a1.6.2-0ubuntu4_i386.deb ...
Unpacking wine1.6 (1:1.6.2-0ubuntu4) ...
dpkg: error processing archive /var/cache/apt/archives/wine1.6_1%3a1.6.2-0ubuntu4_i386.deb (--unpack):
 cannot copy extracted data for './etc/xdg/menus/applications-merged/wine.menu' to '/etc/xdg/menus/applications-merged/wine.menu.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.6_1%3a1.6.2-0ubuntu4_i386.deb
Error in function: 
dpkg: dependency problems prevent configuration of wine1.6-i386:
 wine1.6-i386 depends on wine1.6:any (= 1:1.6.2-0ubuntu4); however:
  Package wine1.6 is not installed.

dpkg: error processing package wine1.6-i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.6 | wine1.7; however:
  Package wine1.6 is not installed.
  Package wine1.7 is not installed.

dpkg: error processing package wine (--configure):
 dependency problems - leaving unconfigured
Setting up mime-support (3.54ubuntu1) ...

```

---

### Post by ian-weisser on 2014-09-10
> ```
failed to write **(No space left on device)**
```

The system seems to think your partition is full.

---

### Post by bobbyallan on 2014-09-10
> **ian-weisser said:**
> The system seems to think your partition is full.

The system seems to be right.
lvm only set me up with a 340mb etc folder.

Thanks.

---

