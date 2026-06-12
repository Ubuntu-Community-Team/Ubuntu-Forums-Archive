---
title: "How to compile my own version of Ubuntu?"
date: 2014-10-01
forum: General Help
---

### Post by Ankush_Menat on 2014-10-01
E.g. I want to deploy Ubuntu on 20 systems all of them preloaded with latest libreoffice, WPS Office and many more FREE software. I dont want to install it manually on all systems.

Is there any way to do this? After searching on web I found Ubuntu-builder but that doesnt seems to support 14.04LTS release.

Something like SUSE Studio (Which can generate custom opensuse version) for Ubuntu would be great IMO.

---

### Post by Bucky Ball on 2014-10-01
I would advise you start with a minimal install, create what you are after, then clone that with clonezilla (create and ISO, the instructions for which you will find below) and do a net install to the 20 computers. Here's some links:

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

And for Clonezilla:

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

If the 20 computers are all on the same LAN it shouldn't be that tricky, but maybe a little time consuming and brain draining, but fun! Life is for learning and living. ;)

---

### Post by ukripper on 2014-10-01
This may help - [http://askubuntu.com/questions/190133/what-are-the-alternatives-for-remastersys](http://askubuntu.com/questions/190133/what-are-the-alternatives-for-remastersys)

---

