---
title: "Need help: Repartitioned ntfs is not mountable/recognizable... :'("
date: 2008-04-02
forum: General Help
---

### Post by ethidda on 2008-04-02
So, long story short, I tried installing ubuntu with a Breezy disk (which failed spectacularly) but then got my hands on a Gutsy version, which is what I'm running now. Anyways, I repartitioned my laptop harddrive with Breezy (there was already 100 megs free space before the windows volume for some reason), and now there are 4 partitions, as follows

/dev/hda1 as /boot (with grub)
/dev/hda3 as original windows partition
/dev/hda4 as /
/dev/hda5 as swap

However, when grub was installed (both times, with Breezy and with Gutsy), it didn't detect the windows volume as bootable. Neither does the partition table recognize it as ntfs. There was no sign of it in the fstab.

Furthermore, I tried the following commands after installation

sudo mkdir /media/windows
sudo mount /dev/hda3 /media/windows -t ntfs-3g

and it complains that it is not a recognizable ntfs file system. And indeed, it seems to think that it is now a linux file system, as doing an fdisk -l returns the following line for the aforementioned troublesome volume

/dev/hda3   *          14        8524    68364607+  83  Linux

I have quite a few important files stored only on that volume without any backup copies and I would like to recover them if possible. Any help for this n00b is therefore much appreciated.

Thanks,
ethidda

EDIT: When I looked at it in gparted, it shows the partition as type "unknown". So I guess something must've seriously damaged it. Is that right? And if that's the case, what's the best thing I can do to recover it?

EDIT2: Okay, I found my disk back using testdisk (which is in one of the additional repositories). It worked, but messed up my grub (error 17). I'm too lazy to figure out how to fix it. So I'm doing yet another install of gutsy, and hopefully it'll work. I'm just happy I have all my windows files back. :D

---

