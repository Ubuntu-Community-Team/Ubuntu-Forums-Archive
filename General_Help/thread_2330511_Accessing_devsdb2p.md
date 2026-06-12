---
title: "Accessing /dev/sdb2p*"
date: 2016-07-12
forum: General Help
---

### Post by Peter_Horn on 2016-07-12
I upgraded a dual-boot machine, which involved repartitioning the disk. Before I did so, I ran dd from the installation CD (16.04LTS) and imaged /dev/sda to an external drive on /dev/sdb2 (the system had already created /dev/sdb1, i think for swap). fdisk tells me that that drive contains /dev/sdb1 and /dev/sdb2, which in turn contains /dev/sdb2p1 thru /dev/sdb2p7, all with the expected size and attributes. So far, so good.
I want to mount /dev/sdb2p6 (the original /) so I can retrieve some stuff from the old ~.

Attempting to mount /dev/sdb2p6:
peter@Orion:~$ sudo mount /dev/sdb2p6 here
mount: special device /dev/sdb2p6 does not exist

Attempting to mount /dev/sdb2:
peter@Orion:~$ sudo mount /dev/sdb2 there
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error


So, how can I mount /dev/sdb2p6, or otherwise access its contents?

---

### Post by Bucky Ball on 2016-07-12
You need to create a mount point.

```
sudo mkdir /media/devsdbp6
sudo mount /dev/sdb2p6 /media/devsdb2
```

/dev/sdb2p6 must be a partition to mount it in your new mountpoint. I've never seen that naming convention before, though. 

Try that. The mountpoint name you create can be anything you want, within reason (limited by the syntax used for this).

Not sure what you mean by sdb2 contains the others. You mean sdb2 is an extended partition? I think that would be sdb5. Could you explain in more details, please? ;)

---

### Post by steeldriver on 2016-07-12
It sounds like you dd'ed a whole disk (/dev/sda) containing multiple partitions, to a single partition (/dev/sdb2) - never done that, not sure what happens

---

### Post by Bucky Ball on 2016-07-12
> **steeldriver said:**
> It sounds like you dd'ed a whole disk (/dev/sda) containing multiple partitions, to a single partition (/dev/sdb2) - never done that, not sure what happens

Ah, that might explain it. Interesting and no, never been there, done that either. :-k

@OP: perhaps you could post the exact dd command you used to do this. Might clear things up a little. On the other hand, if what steeldriver mentions is what you have done, perhaps you could try dd-ing just the partition you want and trying again. 

Perhaps have another read through whatever how-to or tutorial you were using to do this, if you were, and look for a few examples of dd commands that do what you are attempting to achieve.

A birdie also whispered in my ear that this may be an LVM setup. Is it?

---

### Post by Peter_Horn on 2016-07-13
Yes, steeldriver got it right. Looks like I'll have to **dd** just that partition to a virgin media and mount that. Just as well I have hardcopy of the partition table. :p I don't recall the exact **dd** i used but it was something like [B]dd if=/dev/sda of=/dev/sdb2
[/B]
I find it interesting that **fdisk** can see the partition table on /dev/sdb2 but **mount** apparently cannot.

Sorry I didn't mention in my original post, "here" and "there" were directories i'd created in ~ for mount points. 

I don't even know what LVM is, so I don't think it's one of them.

---

### Post by Bucky Ball on 2016-07-13
Yea. This bit:

> dd if=/dev/sda

... points to the WHOLE drive, as I'm sure you've now realised, not a partition (which would have been, for instance and if you were after sda3 say, dd if=/dev/sda3 of=/dev/sdb2). 

I think that would give you a clone of sda3 on sdb2, but don't quote me. I avoid dd (nicknamed 'disk destroyer' for obvious reasons) and use fsarchiver or Clonezilla generally so no dd expert. :)

---

### Post by Peter_Horn on 2016-07-18
Just to tidy things up, i dd'd the partition to a bare disk and all is good. I can mount any of the partitions from there.

---

### Post by Bucky Ball on 2016-07-18
Great news and thanks for marking as solved. Another brain wrinkle and further along the learning curve we go! 

Enjoy Ubuntu-ing. :)

---

