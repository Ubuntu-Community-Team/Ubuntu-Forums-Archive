---
title: "Mysterious out of space messages"
date: 2013-01-04
forum: General Help
---

### Post by jimhenry on 2013-01-04
A couple of days ago I got a pop-up message box saying there was only a few hundred megabytes of free space on my hard drive.  I deleted a few things and emptied the Trash, then checked df; it said my main hard drive was only 93% full (but I think it had said 95% the last time I'd checked it, not long before that error message).  Today I tried to hibernate (I'm using a Dell Inspiron 15n laptop), and got a message about "Not enough free swap".  I checked df again and got similar results:

```

Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1      149745956 131300116  10839160  93% /
udev             2037604         4   2037600   1% /dev
tmpfs             817960       924    817036   1% /run
none                5120         0      5120   0% /run/lock
none             2044892       788   2044104   1% /run/shm
/dev/sdb1       15101952    684416  14417536   5% /media/650B-105B
/dev/sdc1      312570196 292194656  20375540  94% /media/cugel
/dev/sdd1        3969024   1259264   2709760  32% /media/5D18-F276

```In other words, it looks like there's over 10GB free space.  Is there a different partition not showing up there where the swap is supposed to be happening?  If so, how do I figure out why it doesn't have free space and fix it?

I'm using Ubuntu 12.04.

---

### Post by Pjotr123 on 2013-01-04
"Only" 93 % full.... :shock:

A Linux partition, *any* Linux partition, should never be filled over 80 %, because otherwise fragmentation will occur:
[https://sites.google.com/site/easylinuxtipsproject/faq#TOC-How-can-I-defragment-the-hard-drive-in-Linux-](https://sites.google.com/site/easylinuxtipsproject/faq#TOC-How-can-I-defragment-the-hard-drive-in-Linux-)
(item 4, left column)

Sidenote: don't forget that root reserves 5 % by default for itself.

---

### Post by grahammechanical on 2013-01-04
There are two different issues mentioned in your post.

1) The hard disk full message. Which you have attempted to solve. And may be have solved for the time being.

2) The not enough swap space for hibernation.

How much system RAM do you have? How big is your swap partition? I may be wrong but it is my understanding that when we hibernate the machine the contents of system RAM is stored on the hard disk (in swap?). 

> When a computer hibernates, it will save its current state to the hard disk and power down completely. When next the computer boots, the prior state is restored just as you left it. 

[https://help.ubuntu.com/community/PowerManagement/Hibernate]("https://help.ubuntu.com/community/PowerManagement/Hibernate")

> The hibernation feature (suspend-to-disk) writes out the contents of RAM to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size. The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition. It cannot use a swap file on an active file system.

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

Regards.

---

### Post by takuie on 2013-01-04
Looks like a full drive to me, being that close to 100% is only asking for a crash.

And like mentioned before, 5% is held by root. So 93% is actually 98%

---

