---
title: "transferring Ubuntu 12.04 LTS data to external hard disk"
date: 2015-06-30
forum: General Help
---

### Post by tnob on 2015-06-30
Hello all,

My question is a brief one.

On my desktop is dual boot Ubuntu 12.04 LTS/Windows 7 - and an overhaul of this has been long overdue. But before this happens, in two days time,** all **data currently on my system should first be transferred to a 2TB external hard disk with 1.5TB still on it - a Seagate Expansion Drive, incidentally - so that the data can later be incorporated in my new platform. With the command line, this always panned out brilliantly, on previous occasions. 

However, the command line formula 'normally' used has been lost. I can't find it back anywhere. I once got it through a kind soul I can't contact any more. Besides, I'm not really well-versed in CLI myself, so not too sure which commands apply to the situation as sketched above.

Can anybody help me out please? There is some urgency to my request, since I now only have part of an afternoon and one evening available to sort this out. 

Thanks very much.

tnob

---

### Post by Bucky Ball on 2015-06-30
You just want to save personal data? You could try Luckybackup. It's in the repositories. There's a heap of backup software options in Ubuntu. Have a quick search. 

If you want to go for a whole partition or disk, try Clonezilla or fsarchiver. Here are some links for Clonezilla:

Home site:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Your friend probably used the 'dd' option with the terminal command. That can also stand for 'death and destruction' (among other things) as it will completely wipe whatever it is copying to. If you make a mistake with your target and you have valuable data on it, you're cheese. 

You could say the same about any backup really, though. Down to user error, I guess, and I know I've stuffed up on backups on a couple of occasions. If you want to use the terminal then the 'dd' command is probably it and the place to start researching. I'm not game to give you advice with it as only used it once or twice, but someone more au fait with it will no doubt guide you. Good luck.

---

