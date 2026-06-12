---
title: "fsck always finds errors"
date: 2007-03-06
forum: General Help
---

### Post by golem3 on 2007-03-06
I used to turn the 30 mount auto-fsck off (using /etc/fstab) but these days I have put it back on. Why? Fsck always finds errors every 30 mounts...is that normal?

---

### Post by mcduck on 2007-03-06
Could you post your /etc/fstab here? Perhaps there's something wrong with it.. :)

---

### Post by golem3 on 2007-03-06
> **mcduck said:**
> Could you post your /etc/fstab here? Perhaps there's something wrong with it.. :)

Gladly, mcduck. Thanks.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=99414af3-74ab-479d-8ba7-ff69900c0801 /               ext3    defaults,errors=remount-ro 0      1
# /dev/hda5
UUID=f95452ed-057b-417f-a8d1-7fb6d572421d none            swap    sw              0       0

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by mcduck on 2007-03-06
Ok, I don't see anything wrong with your fstab. It could be that either you have bad RAM (run the memtest from the boot menu over night to check that) or your hard disk could be dying.. Most manufacturers have some tools to check the disk condition, you could try that too.

It's normal for fsck to run every 30 mounts, but there really should not be any errors..

Also you could boot with the live-cd and then try to run 'e2fsck /dev/hda1' and see if it can actually fix the errors.

---

### Post by golem3 on 2007-03-06
Ok, thanks. 

So i will run memtest86 & look into the S.M.A.R.T information.

How old is too old, do you think, for a 4200 RPM 100GB drive which began usage in December of 2005?

---

### Post by mcduck on 2007-03-07
> **golem3 said:**
> Ok, thanks. 

So i will run memtest86 & look into the S.M.A.R.T information.

How old is too old, do you think, for a 4200 RPM 100GB drive which began usage in December of 2005?
In my opinion a hard disk should last at least 10 years. I still have one working 8GB disk from 2000, and one 256MB disk from my old 486 machine.. But as life is, you never know, and sometimes you get a bad disk or one that will fail after couple of years.. (that's why it's said that one should always keep backups. Hard disks do not always fail gradually, they can work on one boot and fail on next..)

---

### Post by Mr. C. on 2007-03-07
> **golem3 said:**
> I used to turn the 30 mount auto-fsck off (using /etc/fstab) but these days I have put it back on. Why? Fsck always finds errors every 30 mounts...is that normal?

There are likely to be errors if your system crashes, or you power down by essentially pulling the plug or turning off the switch.

---

### Post by dcstar on 2007-03-07
> **golem3 said:**
> I used to turn the 30 mount auto-fsck off (using /etc/fstab) but these days I have put it back on. Why? Fsck always finds errors every 30 mounts...is that normal?

It **checks** for errors every 30 mounts, errors may well be there for other mounts but you won't know if you don't check for them, will you?

---

### Post by Mr. C. on 2007-03-07
Bad memory will not localize itself to file system corruption.  The OP would see random system crashes, incorrect data, etc. as well.

The ext3 file system is extremely reliable.  If errors are found with fsck each time, it is possible there is a controller / disk problem, or as I mentioned in my first post, inappropriate shutdown.

MrC

---

### Post by golem3 on 2007-03-08
Thanks for confirming my suspicions. 

I am going to be getting a new hard drive anyway (long overdue) and perhaps a fresh Ubuntu install will do the trick.

---

