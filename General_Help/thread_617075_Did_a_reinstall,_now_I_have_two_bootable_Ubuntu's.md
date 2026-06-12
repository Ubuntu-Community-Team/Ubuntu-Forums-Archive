---
title: "Did a reinstall, now I have two bootable Ubuntu's"
date: 2007-11-19
forum: General Help
---

### Post by OvenMitt Bandit on 2007-11-19
I was having some issues with video card drivers, so I just decided to reinstall Ubuntu. They were fine to begin with, then something happened, not exactly sure what, but I just decided to install Ubuntu again to roll back to the previous settings. I thought I was getting rid of the old, and replacing it with the new, but I guess not. I now have two non-XP volumes, one 170 GB and one 105 GB, and there are two choices of Ubuntu at GRUB, the old and the new. Is there a way to get rid of whatever is on the old volume and incorporate it into my new install?

---

### Post by prince_niceguy on 2007-11-19
can you post your fstab and the screen shot of your drive partition from gparted. seems the reinstall created a new partition and installed on that.

---

### Post by OvenMitt Bandit on 2007-11-19
Alrighty, here is the screenie from gparted:

[http://img68.imageshack.us/img68/2168/gpartedscreenik1.png]("http://img68.imageshack.us/img68/2168/gpartedscreenik1.png")

How do find my fstab? I am very new to Linux, I had to use Google to find out what gparted was.

---

### Post by prince_niceguy on 2007-11-19
oh i am sorry.

do in coommandline

$ more /etc/fstab.

if you can login into both ubuntu and paste it it would be great.

---

### Post by teryowen on 2007-11-19
so on which partition is your new ubuntu?

Seems like its on sda3

so if you feel comfortable go ahead and format the other ext3 partition (sda2)

Also you do realize that your first 170GB is ntfs, are you dual booting?

EDIT: you also have 2 linux-swap you should only have one, so delete the sda5 one and use the unallocated space for your ext partition.

---

### Post by OvenMitt Bandit on 2007-11-19
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=3aacc1ce-4e28-4ca9-8e10-69e1ec9c1a8e /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sda6
UUID=7ffb7271-b46e-4aac-aea4-3d28c5d19516 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


There ya go.

And yes, I am dual booting, that NTFS is WinXP.

---

### Post by prince_niceguy on 2007-11-19
OK. now to understand fully ... what you want to do??? do you want to remove the menu item from grub or you want get back the partition which is taking unnecessary space for you?

---

### Post by OvenMitt Bandit on 2007-11-25
I formatted the partition my old Ubuntu was on, now I would like to incorporate that drive space into my new Ubuntu partition. And yes, I would also like to get rid of the old Ubuntu option in grub.

---

### Post by prince_niceguy on 2007-12-11
Sorry was out for some time...

to get rid of the grub menu first...

run the following command

sudo update-grub

Hopefully this should remove the redundant entry.

Next we will take up the recovering of space if it is not done already.

---

### Post by OvenMitt Bandit on 2007-12-20
Alrighty, I just ran the grub updater. I guess I'll see if it worked next reboot.

---

### Post by prince_niceguy on 2007-12-20
seems your sd2 partition is redundant. you can safely format that partition or make it unallocated using gparted.
once done you will have retained your disk space.

now only thing which is not known to me is where is your grub installed. I am not sure how to find it. will let you know after some help from some one in the forum.

till then do not delete the sda2 partition.

---

