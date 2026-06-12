---
title: "How to unmount /var/lib directory"
date: 2007-10-11
forum: General Help
---

### Post by mmathur on 2007-10-11
I have Feisty setup with my /var/lib as the mount point for a LVM.  I want to add another hard drive to my LVM, but in order to do this, I will need to un-mount the /var/lib directory.

How can I unmount the /var/lib directory or mount point on my machine since once Ubuntu starts up and I log in, some processes are using the data stored within that mount point and therefore it is always busy??

Here is what I get when I try to un-mount /var/lib:
~$ sudo umount /var/lib
umount: /var/lib: device is busy
umount: /var/lib: device is busy

Thanks in advance for your help.

BTW, I'm using the following guide on LVM to help me out with this...it was very helpful when I initially setup my LVM:
[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

---

### Post by dcstar on 2007-10-11
> **mmathur said:**
> I have Feisty setup with my /var/lib as the mount point for a LVM.  I want to add another hard drive to my LVM, but in order to do this, I will need to un-mount the /var/lib directory.

How can I unmount the /var/lib directory or mount point on my machine since once Ubuntu starts up and I log in, some processes are using the data stored within that mount point and therefore it is always busy??

Here is what I get when I try to un-mount /var/lib:
~$ sudo umount /var/lib
umount: /var/lib: device is busy
umount: /var/lib: device is busy

Thanks in advance for your help.

BTW, I'm using the following guide on LVM to help me out with this...it was very helpful when I initially setup my LVM:
[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

/var/lib is a system directory, you should never need to unmount it because YOU should never be using it in this manner.

The LVM HOWTO says nothing whatsoever (that I can find) about using /var/lib as a mount point.

Try booting up in Recovery mode (and I still doubt that this will work) and change your LVM setup so you are no longer using /var/lib in any manner whatsoever.

---

### Post by mmathur on 2007-10-11
Not exactly the answer I was looking for...

The reason I setup my LVM as such was because I was following guides on how to setup MythTV and I created a partition and setup /var/lib as the mount point for that partition.  Earlier this year I ran out of disk space on that partition due to all the media I collected. I then moved to an LVM setup with the mount point to be /var/lib.  And now, i'm in the same position where I've collected so much media and need to expand my LVM.

In the past I used a Gparted boot disk to setup the original LVM and I was hoping to avoid having to use a boot disk, but so far it sounds like that is my only option.

---

### Post by mmathur on 2007-10-15
So booting with the GParted boot disk didn't do the trick.  My /var/lib directory got completely corrupted.

I am planning on rebuilding my system and setting up the partitions as follows:

Partition 1 - 10GBs Mount Point: /
Partition 2 - 2GBs as Swap
Partition 3 - 20GBs Mount Point: /var/lib
Partition 4 - 1.5TBs as LVM Mount Point: /var/lib/mythtv

Would there be any issues with creating a directory under /var/lib which will be the mount point for my LVM partition?

I'd appreciate any advice since this is my 3rd time rebuilding this system and I'd like to get it to a state where I can easily add additional storage if needed.  Thanks.

---

