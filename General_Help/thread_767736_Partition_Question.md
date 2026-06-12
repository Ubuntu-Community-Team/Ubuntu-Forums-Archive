---
title: "Partition Question"
date: 2008-04-25
forum: General Help
---

### Post by Gauvenator on 2008-04-25
I have my computer partitioned like this:
```
$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d5b49ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        6079    29294527+  83  Linux
/dev/sda3            6080        6565     3903795   82  Linux swap / Solaris
/dev/sda4            6566       13859    58589055    5  Extended
/dev/sda5            6566       10212    29294496   83  Linux
/dev/sda6           10213       13859    29294496   83  Linux
```

Does this mean all 4 possible primary partitions are used up?  I wanted to put Ubuntu in an extended, but I didn't have the option during installation.  Is there a way to change that?

Also, is it OK to use the Gparted to make more partitions while Ubuntu is running?  Or should I just boot off the CD?

---

### Post by Aearenda on 2008-04-25
Yes, all 4 primaries are used - sda1,2,3 are regular primary partitions, sda4 is the last primary partition which contains the extended partitions sda5 and 6. You can tell this by looking at the start and end points for sda5 and 6 - they overlap sda4.

It should be possible to use sda5 or 6 to install Ubuntu using the manual partitioning option. You may need to use the alternate install CD to get the maximum flexibility - I always use the alternate CD, so I haven't done a 'standard' setup from the live CD recently - it may be possible there too. However, GRUB needs a primary boot partition somewhere. If you already have GRUB elsewhere (on a previous Linux installation, perhaps), you can install Ubuntu's GRUB in the same partition as Ubuntu itself, and chainload it from the other one.

You can add partitions if you have free space, or change or delete **unmounted** partitions, when Ubuntu is running from a different partition on the same or a different drive. However, in the fdisk output shown, there is no free space left. If the extended partition sda4 does not use all the remaining space on the drive after sda1,2,3 are set up, then the rest is unusable.

So, what do you already have installed, and what are you trying to achieve?

---

### Post by Gauvenator on 2008-04-25
> **Aearenda said:**
> Yes, all 4 primaries are used - sda1,2,3 are regular primary partitions, sda4 is the last primary partition which contains the extended partitions sda5 and 6. You can tell this by looking at the start and end points for sda5 and 6 - they overlap sda4.

It should be possible to use sda5 or 6 to install Ubuntu using the manual partitioning option. You may need to use the alternate install CD to get the maximum flexibility - I always use the alternate CD, so I haven't done a 'standard' setup from the live CD recently - it may be possible there too. However, GRUB needs a primary boot partition somewhere. If you already have GRUB elsewhere (on a previous Linux installation, perhaps), you can install Ubuntu's GRUB in the same partition as Ubuntu itself, and chainload it from the other one.

You can add partitions if you have free space, or change or delete **unmounted** partitions, when Ubuntu is running from a different partition on the same or a different drive. However, in the fdisk output shown, there is no free space left. If the extended partition sda4 does not use all the remaining space on the drive after sda1,2,3 are set up, then the rest is unusable.

So, what do you already have installed, and what are you trying to achieve?

I've actually already installed Ubuntu on sda6.  Currently I have Arch64 (Sda1), Mint(Sda5), and Ubuntu(Sda6) installed.  Sda2 is a home partition for Arch.

In the future I will be installing Fedora 9, and I was wondering if I've eaten up all the partitions.

So is there a way to move partitions around so I can put the extended last and resize it?    I'm OK with destroying a partition if necessary-I don't really need Mint.

---

### Post by sandysandy on 2008-04-25
> was wondering if I've eaten up all the partitions.
 u can use gparted to resize ur logical partitions within the extended partitions and in the free space thus generated create another partition.

u can also resize the neighboring primary partitions and thereafter expand ur extended partition. 

see this link

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by Gauvenator on 2008-04-25
Thanks for you both!

I resized it and now there is free space.

---

### Post by Aearenda on 2008-04-25
OK, the extended one IS last - that's sda4. It's a container for sda5 and sda6, which are 'logical' partitions - kind of like a cabinet with 4 drawers, the last of which has a fixed divider in it making 5 usable spaces in all - like this:

```
-----------start of disk------------
|              sda1                |
|              arch                |
------------------------------------
|              sda2                |
|           arch /home             |
------------------------------------
|              sda3                |
|           swap for all           |
------------------------------------
|     sda4 - extended partition    |
|     sda5       |     sda6        |
|     Mint       |    Ubuntu       |
------------End of disk-------------
```

I think you could resize sda5 and 6 from Arch, so long as you don't have them mounted; or just boot off a live CD as you originally suggested.

Otherwise, all I would do to install Fedora is install it in sda5, reformatting on the way to get rid of Mint. Be careful about installing the boot loader (but you must have worked that out already), and about reformatting the swap partition - Ubuntu at least will be identifying it by UUID instead of by /dev/sda3, unless you have changed it, and if it is reformatted the UUID changes.

Edit - I see you have already resized - great! Problem solved.

---

