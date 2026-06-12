---
title: "Unable to mount HFS external"
date: 2007-09-12
forum: General Help
---

### Post by arcticblue on 2007-09-12
I've Googled for a solution to my problem, but couldn't find much in English.  What I did find in English required modifying the fstab and that shouldn't be necessary for an external drive.  Anyway, on with my problem...

I tried out Kubuntu Gutsy over the past few days and it works great.  It mounted my HFS formatted external hard drive just fine when I clicked on the device icon in Dolphin.  Well, I decided to go back to Feisty until Gutsy is finished and my external isn't mounting any more.  I get this error when I try to mount it: "hal-storage-fixed-mount-all-options refused uid 1000".  Typing "mount /dev/sdb3 /mnt/tmp" (there's an sdb1 through sdb4 but the only real partition on it is sdb3) as root works fine, but this is 2007 and I know that automounting *should* work.

Thanks in advance for the help.

---

### Post by arcticblue on 2007-09-12
Just wanted to let everyone know I fixed it.  The solution was to disable "Mount as User" under the device properties in Konquerer.  I found that a bug had been filed on launchpad about this issue ( [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/110210](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/110210) ).  Evidently, this bug was introduced in Feisty and was reported in April.  Feisty has been out for a while...  has anyone even looked in to this?

---

