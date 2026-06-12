---
title: "Unite partitions?"
date: 2008-05-24
forum: General Help
---

### Post by GabrielWolff on 2008-05-24
I have saved some 70GB on a machine for a possible WIN installation. As I am sure now I will never have to use that space for evil, I'd like to open that space for usage under Ubuntu.

So what I did was formatting the partition and now it is usable as another Volume on the machine.

But I have to mount it manually after booting, and this isn't my machine, I'd rather have it made as clean as possible

I would like to
either unite the original partition and the new one (preferably)
or have the partition to boot automatically at startup

How do I do that?

Thx

---

### Post by forestpixie on 2008-05-24
Make a folder for it to mount in and add it to fstab.

---

### Post by GabrielWolff on 2008-05-24
> **forestpixie said:**
> Make a folder for it to mount in and add it to fstab.

No chance to unite the partitions? The new one is empty. Could I erase it and enlarge the other one?

---

### Post by forestpixie on 2008-05-24
Oh yea - sorry you can do that if you want - use the livecd it's got a partition editor on it, or download and burn gparted or partedmagic then you can boot with them, burn as iso/image not data - I prefer to use a bootbale partition editor myself.

It depends on how the partions are on the disc as to how to go about it.

Post the result of this if you're not sure

```
sudo fdisk -l
```

---

### Post by GabrielWolff on 2008-05-24
Here we go:

```
Vnuphar@nuphar-laptop:~$ sudo fdisk -l
[sudo] password for nuphar: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4867    39094146   83  Linux
/dev/sda2            4868        4989      979965   82  Linux swap / Solaris
/dev/sda3            4990       14593    77144130   83  Linux

```

So what should I do?

---

### Post by forestpixie on 2008-05-24
I assume that it's the end partition - sda3.

I would as I've said use a bootable editor, personally I use [partedmagic]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads") now after having problems with [gparted]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779"), but I believe it's better now.

You need to do a few things - do them seperately, apply changes at each stage.

Delete your new partition so that it is unallocated space.
Move the unallocated space so that it is next to sda1.
Resize sda1 to take up the unallocated space.

Be aware that there is a possibility of data loss - you're playing with partitions, backup if necessary - I'm not saying that it will happen but it could.

When you boot you might have a problem with changed UUID - if you get a grub error 8 that is what it is - but that is easily solved.

Finally it could take a long long time to finish.

If you have any other questions ask before you start :)

---

