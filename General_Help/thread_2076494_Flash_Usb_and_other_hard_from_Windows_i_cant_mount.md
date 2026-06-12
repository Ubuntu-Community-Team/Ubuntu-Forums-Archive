---
title: "Flash Usb and other hard from Windows i cant mount with 12.10"
date: 2012-10-26
forum: General Help
---

### Post by cutiyar on 2012-10-26
hi
after upgrading from 12.04 to 12.10 , now i cant mount other two partition that are windows installed on it ,  and i cant mount my sdcard with my android and other flash disc, whats wrong? giving this error :

---

### Post by bart.a on 2012-10-26
Are they all formated as exFat?

---

### Post by cutiyar on 2012-11-02
no they are in ntfs format.

---

### Post by Bucky Ball on 2012-11-02
**@ cutiyar: **I have edited the giant screenshot in post #1 to be an attachment. You may wish to edit your text accordingly.

Pics should be either an attachment (smaller the file the better) or a thumbnail. Thanks. ;)


PS: Are you sure you have the correct, matching mount point in /media and /fstab files? Other thing is partitions are probably NTFS filesystem so you may need to install ntfs-3g and ntfs-config then run from your apps menu. That would take care of writing the fstab and giving the partitions the correct permissions.

---

### Post by cutiyar on 2012-11-02
in 12.04 i did mounting from nautilus and no problem now i cant ad show this error.

---

### Post by Bucky Ball on 2012-11-02
> **cutiyar said:**
> in 12.04 i did mounting from nautilus and no problem now i cant ad show this error.

It worked fine in 12.04 LTS but the last part is a little unclear ... ;)

Just out of curiousity, was there a particular reason you upgraded to 12.10? 12.04 LTS is the five year long-term support release and stable in comparison (as you probably know). 12.10 has only been out only 2-3 weeks. Expect breakages and niggling oddities for a while.

---

### Post by cutiyar on 2012-11-04
thanks all ,i have downgraded to ubuntu 12.04 LTS and no problem, iam using ubuntu since 7.10 i didn't see the slower and bad version like  ubuntu 12.10 .
FULL OF BUG.

---

### Post by kyouren on 2012-11-08
I found this in another post. In a "Terminal", try entering:
  sudo mkdir /media/${USER}
  If you have other users on the same machine, say, fred, create /media/fred as well
  Amazing that such a basic issue was not addressed before 12.10 was released!

---

