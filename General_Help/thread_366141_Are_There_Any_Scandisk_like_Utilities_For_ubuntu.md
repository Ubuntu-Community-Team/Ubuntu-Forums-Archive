---
title: "Are There Any Scandisk like Utilities For ubuntu"
date: 2007-02-20
forum: General Help
---

### Post by cpuwhiz11 on 2007-02-20
Greetings, I have ubuntu 6.06 and I was wondering if there are any disk repair programs like Microsoft's Scandisk that I could get for ubuntu. Something that would scan both my computer's hard drive and an external hard drive for errors and fix them. Also are there any defrag programs as well. Any help you could offer would be most appreciated.

PS. If its buried in some menu that I never found than I apologize for not looking hard enough.

---

### Post by TheWizzard on 2007-02-20
e2fsck
[http://rescuecd.sourceforge.net/](http://rescuecd.sourceforge.net/)

---

### Post by hikaricore on 2007-02-20
Linux checks discs automatically after 30 drive mounts. You'll also find that defragging isn't really necessary as much under linux if you're using ext2 or ext3 based file systems, which handle data storage much more efficiently than fat or ntfs systems.

---

### Post by WinterWeaver on 2007-02-20
I know that Ubunut automatically scans the disks after it's been mounted a certain amount of times, but in your case you probably need something else. Myself I don't really know of many scandisk apps, because I dont really use em.

On the Defrag side, I can say that you don't generally need to defrag your drive when using Linux and the ext3 Filesystem, because the system does not get fragmented easilly. But even thought the ext3 filesystem is this very good in this regard, there are certain things that can still fragment the drive (like Torrent Downloads etc). Here is a link to a forum with a defrag tool:
[http://www.ubuntuforums.org/showthread.php?t=169551](http://www.ubuntuforums.org/showthread.php?t=169551)

Hope this helps ^_^

WW

---

### Post by cpuwhiz11 on 2007-02-20
Thanks for the help

---

