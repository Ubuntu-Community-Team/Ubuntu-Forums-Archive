---
title: "Partitions"
date: 2007-01-02
forum: General Help
---

### Post by Mr. Matt on 2007-01-02
I got a 250MB HD for Xmas and installed Kubuntu 6.10 on it without any partitions other than the swap.

Now I would like to make a few other partitions where I can install Windows and some other Linux distros to test them out.  Also I read a post where one guy says he keeps his Home directory in a separate partition.  I would like to set this up as well.

I thought I read that it is possible to make new partitions without formatting but I can't find a way to do that with Gtparted.

How can I make new partitions on my hda drive?  Currently there is about 190 GB free space and it is ext3 FS.

Thanks

---

### Post by goodfella on 2007-01-02
How is your drive setup?  From your response it sounds like you have two partitions.  The swap partition and / partition with your home directory on the / partition.  If all the space on your drive is allready partitioned and formated then you are going to have to resize the partitions.  But I don't want to make any assumptions so if you could post the information printed from typing
```
df
``` in a terminal it will give me a better picture.

---

### Post by Bartender on 2007-01-02
Check out S Roy's blog.  I don't have broadband so he put these guides up for me. 

[http://www.sroyc.blogspot.com/](http://www.sroyc.blogspot.com/) 

The first guide is for installing PCLOS.  The second one uses GParted (not QTParted) to partition a HDD that already had one Linux distro.  Custom made for your situation if you can get ahold of a copy of [GParted]("http://gparted.sourceforge.net/livecd.php")!

So if you followed the second guide to partition your HDD, you could turn right around and use the first guide to install PCLOS to the new partition.  Take a look thru the PCLOS guide even if you don't want to install that.  I went into some detail about how to chainload the second Linux, and what to do with the bootloader.  That part is applicable to most any Linux distro.

---

### Post by Mr. Matt on 2007-01-02
Hi goodfella,

Here is the output of that command:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1            237943776  32784648 193072228  15% /
varrun                  420292        80    420212   1% /var/run
varlock                 420292         0    420292   0% /var/lock
procbususb               10240       128     10112   2% /proc/bus/usb
udev                     10240       128     10112   2% /dev
devshm                  420292         0    420292   0% /dev/shm
lrm                     420292     17580    402712   5% /lib/modules/2.6.17-10-generic/volatile
/dev/hdb1             15020272   7449848   7570424  50% /media/hdb
```

---

### Post by bodhi.zazen on 2007-01-02
Boot to a live CD, Ubuntu or Gparted.

Resize your current Kubuntu partition (make it smaller) with gparted.

In the resulting free space, partition away .....

---

