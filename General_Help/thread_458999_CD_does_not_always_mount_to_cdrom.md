---
title: "CD does not always mount to /cdrom"
date: 2007-05-30
forum: General Help
---

### Post by SteveF on 2007-05-30
I just updated the kernel for Feisty (to 2.6.20-16.  I didn't notice before (so not positive if it is a new kernel question or just Feisty), but now not all CDs mount to /cdrom.  I just burned a cdrw and it mounted to /media/work.

Is this how Feisty will start mounting CDs?

Thanks,

Steve

---

### Post by kernel tom on 2007-05-30
can't think of a reason why they would have changed it.  if it bothers you just edit ur fstab file...

sudo nano /etc/fstab

---

### Post by trincamckee on 2007-05-30
Im having the same problem with the last kernel update, when i mount some cdrom, one new entrie is created on */media* with the cdrom label name. For example if cdrom as the name of *bin* it will be mounted on */media/bin* in spite of */media/cdrom0* or */media/cdrom1*. I dont have any idea why this is happening, i hope ubuntu dev will correct this, meanwhile kernel 2.6.20-15 will be my choice.

---

### Post by SteveF on 2007-05-30
> **trincamckee said:**
> Im having the same problem with the last kernel update, when i mount some cdrom, one new entrie is created on */media* with the cdrom label name. For example if cdrom as the name of *bin* it will be mounted on */media/bin* in spite of */media/cdrom0* or */media/cdrom1*. I dont have any idea why this is happening, i hope ubuntu dev will correct this, meanwhile kernel 2.6.20-15 will be my choice.

When I right-click on a CD, I see I can set the mount name.  It does state it will use the volume label if one exists, but can be overridden.

I actually like this (as long as I control the volume label name).

One thing I noticed was that after the update, the device changed back to /dev/hdc.  After Feisty upgrade, it had changed to /dec/scd0.  Now with the change back, I had to modify fstab.  But the CD drive is working better now.

Steve

---

