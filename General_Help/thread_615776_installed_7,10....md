---
title: "installed 7,10..."
date: 2007-11-17
forum: General Help
---

### Post by r0tor on 2007-11-17
I've been using Wubi and the 7.04 version for awhile now and decided to upgrade to 7.10 after Automatrix crashed my old install.  The 7.10 install worked well, but...

- I can't seem to find the windows partition or mount it.  When I do a fdisk-l i see the dev/sda1 drive but i'm unable to find it in the my computer menu.  I tried using the ntfs-config tool i used in the 7.04 days and it seems like its working but again the windows partition does not show up anywhere on the desktop or places menu.

- i also get errors when trying to download many of the supported applications.... like gftp gives me a "gFTP cannot be installed on your computer type (i386)" and VLC player tells me there is a conflict with other software.  Never saw this before - is it wubi problem or gusty problem ?:confused:

---

### Post by r0tor on 2007-11-17
never mind on the windows partition... found it -smacks head-


I am confused about this though... I did a 15GB install and the root directory is showing 8 GB free, but when I go to the home directory it only has 1.7GB free.  Seems confusing to me...

---

### Post by ago on 2007-11-19
> **r0tor said:**
> never mind on the windows partition... found it -smacks head-


I am confused about this though... I did a 15GB install and the root directory is showing 8 GB free, but when I go to the home directory it only has 1.7GB free.  Seems confusing to me...

Probably root and home are installed on separated virtual devices

---

### Post by road2elysium on 2007-12-01
> **r0tor said:**
> 
- i also get errors when trying to download many of the supported applications.... like gftp gives me a "gFTP cannot be installed on your computer type (i386)" and VLC player tells me there is a conflict with other software.  Never saw this before - is it wubi problem or gusty problem ?:confused:

Under Add/Remove Software --> Preferences --> Make sure the (main) Canonical open-source supported software is checked for Downloadable from the internet.

For some reason, it didn't get auto-enabled on one of my installs of Gutsy but it did with another.  After restarting Add/Remove and updating the package list, you'll be able to install gFTP.

---

