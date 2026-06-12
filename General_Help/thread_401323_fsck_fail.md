---
title: "fsck fail"
date: 2007-04-04
forum: General Help
---

### Post by mrmonday on 2007-04-04
Hi everyone,

I have just booted my PC, and got the 'you have mounted 30 times without checking, force checked' message. Somewhere towards the end, I got FAIL, then some instructions. Before I could read them, My PC restarted, and booted normally. these are the contents of /var/log/fsck:

checkroot:

> Log of fsck -C -a -t ext3 /dev/sda2 
Wed Apr  4 18:28:06 2007

fsck 1.39 (29-May-2006)
/dev/sda2: clean, 179662/3997696 files, 1232859/7992337 blocks

Wed Apr  4 18:28:06 2007
----------------

check fs:

> Log of fsck -C -R -A -a 
Wed Apr  4 18:28:06 2007

fsck 1.39 (29-May-2006)

Wed Apr  4 18:28:06 2007
----------------

As you can see neither report any errors. Should I be worried, or has it sorted the problems? Why hasn't it logged the failure?

Thanks

---

