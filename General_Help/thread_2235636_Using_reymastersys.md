---
title: "Using reymastersys"
date: 2014-07-22
forum: General Help
---

### Post by PotatoHead007 on 2014-07-22
Hello :)

I want to backup my whole OS, including installed programs etc. (I have many installed, and my internet would take ages to download everything again), because i will be installing Windows 7 for a dual boot. I found a guide for using reymastersys to achieve this: [http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)
I see that it is an old guide, so i was wondering, does it still apply for Ubuntu 14.04?
Any help appreciated :)

---

### Post by yancek on 2014-07-22
The developer stopped as it was too difficult to keep up with for one person.  You can probably find detailed reasons at the remastersys site if you want.  I saw a post here recently indicating that others were trying to continue it but under a different name.  Unfortunately, I don't have it bookmarked.  The last ubuntu I used it on successfully was 12.04 and haven't tried in on anything newer.

You should do a backup before installing windows 7.  I would hope that during the windows 7 installation you would have an option to install it to a specific partition and although it will overwrite the mbr automatically, you can easily repair that with an Ubuntu CD/DVD.

---

### Post by Karlchen on 2014-07-22
Hello, PotatoHead007.

The development of Remastersys has been stopped. The Remastersys repository may or may not be still available. It definitely does not hold a version tested on Trusty.
Remastersys has been taken over by a developer whose name is Robert Dohnert. Remastersys will be continued under the name of Blacklab-Image-Creator.
The last Remastersys .deb packages can be found here: [Remastersys 3.0.4-2]("http://sourceforge.net/projects/os4systemimage/files/Remastersys%203.0.4-2/").
Personally I have used Remastersys  3.4.0-2 and created a system backup of Linux Mint 14. Have not tried it on anything more recent. So I cannot really tell whether it will give you a usable Trusty Tahr system backup.
But you might try and report back. :wink:
Alternatively you might give the Remastersys fork Blacklab-Image-Creator a try. Its developer states it were ready for Trusty Tahr: [Black Lab Image Creator 1.3 released]("http://system-imaging.blogspot.de/2014/07/black-lab-image-creator-13-released.html")

Kind regards,
Karl

---

### Post by PotatoHead007 on 2014-07-22
Thank you guys :) i shall follow up on everything once i download a legal ISO of Windows 7 (i already have my installation key from my previous Computer).
I am not sure if you can select what partition to install Windows under, some say you cannot. I will follow this up :)

---

### Post by PotatoHead007 on 2014-07-22
Turns out you can install Windows after Ubuntu :)
[http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu](http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu)

---

### Post by Bucky Ball on 2014-07-22
Windows after Ubuntu not a problem. You might like to try Clonezilla to back up your partitions, or even your entire drive. You can then restore the partitions exactly as they were to new partitions of the same size or larger.

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

---

