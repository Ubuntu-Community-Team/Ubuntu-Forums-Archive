---
title: "Transfering Wubi to another harddrive"
date: 2007-09-08
forum: General Help
---

### Post by jshbbe on 2007-09-08
I currently have Wubi installed on an external harddrive, but I would like to move it to my internal harddrive.  I am wondering if it is possible for me to just copy and paste the files over, or do I have to uninstall and reinstall?  If I do copy it over to my internal harddrive, do I have to tell my computer where to find Wubi again?  I know that if I try to boot into Wubi it would probably still look for it in my external harddrive.

---

### Post by tuxcantfly on 2007-09-08
plug in your internet hard drive, make a new partition, and use LVPM [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) to transfer your install over to the new partition

---

### Post by jshbbe on 2007-09-08
Thanks for the reply, but I'd rather not make a new partition for Ubuntu.  I'm using Wubi because I like the fact that I don't have to partition my hard drive.  I guess I'll just leave it on my external hard drive for now.  It is a pain having it on my external hard drive though because if my computer has been off for a while I have to first boot into Windows for some reason.  I really haven't used Ubuntu in a few weeks due to being back in college, but I'd like to start using it again.  Maybe sometime I'll be brave enough change it to a real partition.

---

### Post by ago on 2007-09-09
copy over the c:\wubi\disks folder somewhere else. Uninstall, and reinstall. Then copy the disks folders over the existing one.

---

