---
title: "Is it possible to use Windows programs through Ubuntu 8.04?"
date: 2008-06-03
forum: General Help
---

### Post by smithg86 on 2008-06-03
I read somewhere that it is possible to run/install windows programs through Ubuntu 8.04. (I am trying to use Maple 11, which is only offered for windows xp/vista and mac OS X.) For some reason, they don't offer a Linux version of the program. Is it possible for me to use this program with Ubuntu 8.04, or do I need to run it through windows? I have Windows XP and Ubuntu 8.04 dual-booted on my laptop, if that makes a difference. Sorry if this is a noob question, but I've only had Ubuntu for a few days.

---

### Post by z0mbie on 2008-06-03
Windows Application run under Wine. Here is [the status of Maple 11]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7364&iTestingId=10183") under Wine.

---

### Post by EXCiD3 on 2008-06-03
You can run some, but not all windows programs in Wine > [http://winehq.org](http://winehq.org)

Otherwise you can use a virtual machine to install windows inside linux and then your software inside of that.

---

### Post by kostkon on 2008-06-03
Yes, you can. You'll need to install *Wine*.

[Here]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=98") you can check how well *Maple* runs in *Wine*.

---

### Post by Lecter on 2008-06-03
WINE

It allows using Windows programs through Linux,
also ubuntu aint having the newest NTFS-3G, you should make sure you're using the newest Wine and ntfs-3g stable versions.

NTFS-3G allow Linux to write/read on your windows partition.
I have to mention Ubuntu aint using the newest stable ntfs-3g...

---

### Post by geirha on 2008-06-03
[Wine](https://help.ubuntu.com/community/Wine) can run some windows applications. 

However this page suggests that there are linux versions of maple 11 ... 
[http://maplesoft.com/support/downloads/m11-02_installation.aspx](http://maplesoft.com/support/downloads/m11-02_installation.aspx)

---

### Post by EXCiD3 on 2008-06-03
lol, well enough answers telling you to check out wine, anyone else care to mention wine?

thats the special thing about the forums, everyone is so helpful! :D

---

