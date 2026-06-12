---
title: "Mounting an SFS hard drive under ubuntu"
date: 2013-07-12
forum: General Help
---

### Post by Clanstyles on 2013-07-12
I'm running Ubuntu 13.04. I have two 1TB drives which have data on them I need. However, they were created under my old windows partition (which no longer exists). The drive is formated as an SFS Microsoft Dynamic disk. Automount / mounting it as an NTFS doesn't seem to be working. I've heard some people say it's mountable / fixable and others say I'm screwed and I should just install Windows and then change the format of it. 

Thanks for your time guys.

---

### Post by Cheesemill on 2013-07-12
You'll need to convert it back to a basic disk if you want to access it from Ubuntu as Linux doesn't support Microsoft Dynamic Disks.

The official word from Microsoft is to backup all your data, reformat, and then restore from your backup. However there are other methods you can use which should keep all of your data intact, usually involving booting from a CD containing partition management software. For more details check out this thread on the Windows 7 forums...

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by rodrigokay on 2013-09-09
life got better - now you can [http://packages.ubuntu.com/km/saucy/otherosfs/ldmtool](http://packages.ubuntu.com/km/saucy/otherosfs/ldmtool)

enjoy

rod

---

