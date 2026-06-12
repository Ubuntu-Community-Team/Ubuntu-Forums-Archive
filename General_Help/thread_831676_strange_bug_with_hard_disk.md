---
title: "strange bug with hard disk"
date: 2008-06-17
forum: General Help
---

### Post by va1en0k on 2008-06-17
Hi all.

(Sorry for my very bad english)
7
I have a hard disk drive, connected to PC by USB.
One week my Xubuntu worked fine (drive mounted himself to /media/xaxa), but today I accidentally pulled out the lead from the disk, and then i insert it back, in the /media/ emerged three folders:
/media/xaxa
/media/xaxa_
/media/xaxa__
in /media/xaxa__ was content of my disk

va1en0k@lobstercomp:/media$ ls
cdd  cdrom  cdrom0  floppy  floppy0  hda5  hdc1  History  &#1093;&#1072;&#1093;&#1072;  &#1093;&#1072;&#1093;&#1072;_  &#1093;&#1072;&#1093;&#1072;__
va1en0k@lobstercomp:/media$ cd xaxa
bash: cd: xaxa: No such file or directory
va1en0k@lobstercomp:/media$ rm xaxa
rm: &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1091;&#1076;&#1072;&#1083;&#1080;&#1090;&#1100; `xaxa': No such file or directory
va1en0k@lobstercomp:/media$ sudo rm xaxa
rm: &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1091;&#1076;&#1072;&#1083;&#1080;&#1090;&#1100; `xaxa': No such file or directory

after reboot nothing had changed

I need to get my disk into /media/xaxa ! Please, help me.

---

### Post by TeoBigusGeekus on 2008-06-17
This was an old bug that has been fixed by now.
Have you installed all the updates on your system?

---

### Post by va1en0k on 2008-06-17
yes, of cource

---

### Post by TeoBigusGeekus on 2008-06-17
[http://ubuntuforums.org/showthread.php?t=745832]("http://ubuntuforums.org/showthread.php?t=745832")
and
[http://ubuntuforums.org/showthread.php?t=744469]("http://ubuntuforums.org/showthread.php?t=744469")

---

