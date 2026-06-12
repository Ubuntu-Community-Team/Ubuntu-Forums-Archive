---
title: "Hardware crash, now Ubuntu messed up"
date: 2007-05-12
forum: General Help
---

### Post by JimmyME on 2007-05-12
I used the latest GPARTED Live CD and checked/repaired my partitions and am back to normal.  Thanks for the help Herman!


I had a lockup (no mouse or keyboard) while using Firefox in Ubuntu 6.10 and now have serious problems.  I believe the lockup was due to a hardware situation and not Ubuntu.

I had to shutdown the computer by holding in the power button as the mouse and keyboard wasn't responsive in Ubuntu.

I now cannot open Firefox or Nautilus or most any other program.  If I start in recovery mode it state File System Check Failed, log stored in /var/log/fsck/checkfs  Please repair file system manually.  I can then enter the command line/shell after I enter my root password.

I have no idea what to do to correct this problem and am looking for guidance.

Thanks much,

Jim

---

### Post by JimmyME on 2007-05-13
Bump

---

### Post by Dropbear on 2007-05-15
i recently had a similar problem which caused ubuntu to drop to a maintainence shell when booting. After a lot of mucking around I found running > fsck -y as root several times fixed my system. Like yours I suspect my problem was hardware related.

---

