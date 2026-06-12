---
title: "How to clone install to a new hard drive?"
date: 2005-07-06
forum: General Help
---

### Post by sgarman on 2005-07-06
Hey there,

The hard drive in my workstation is starting to show some SMART errors that I'm concerned about. It's a 120 GB Maxtor. I have a new 160 GB drive which I'd like to replace it with, and my goal is to clone the current drive onto the new one. It will be running in the same computer so the hardware will be the same and no configuration options will change. I am running Hoary Hedgehog.

What's the safest way to do this? I understand that it's not a good idea to try directly copying files in /dev, /sys, and /proc. I also can't just use dd since the new drive does not have the same geometry as the original. 

I tried to check out Partition Image but their web site is down at the moment.

I'd greatly appreciate any advice the community can offer. 

Thanks,

Scott

---

### Post by jeremy on 2005-07-07
I use Partimage for this: [www.partimage.org](www.partimage.org) <- down at the time of writing, try: [http://freshmeat.net/projects/partimage/](http://freshmeat.net/projects/partimage/)

Partimage is in the repositories, but my preferred method is running it from knoppix.

---

### Post by sgarman on 2005-07-08
Thanks, good point. I installed parition image and used it to successfully image and copy my root filesystem partition to the new hard drive. However, I'm having problems with my bootloader when I try to boot from the new drive. 

Partition image has an option for copying the MBR to another drive, but that only works if the partition tables on the two drives are identical. In my case, since the new drive is larger than the old, it refuses to work.

So I tried booting from a CD distro (Knoppix) and running "grub-install /dev/hda". I received an error message regarding the /boot directory and so I mounted the drive, chroot'ed it at the mount point, and tried running grub-install /dev/hda again, but it complained about the stage1 file. I have confirmed that this file is readable.

If I try doing fdisk -l /dev/hda when I'm in the chroot jail it tells me that it doesn't see anything. I'm guessing that's my problem. Does anyone have any more pointers?

Thanks for your time,

Scott

---

### Post by jeremy on 2005-07-08
I'm afraid that I can't help you here, I did this once (cloned to a larger drive) and all went well for me. Hopefully someone else can help.

---

