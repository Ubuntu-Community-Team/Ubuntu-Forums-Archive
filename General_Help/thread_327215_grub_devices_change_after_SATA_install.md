---
title: "grub devices change after SATA install"
date: 2006-12-28
forum: General Help
---

### Post by rpkehoe on 2006-12-28
I recently added a 500 gig SATA drive to my system (thanks Santa) that I wanted to make this my primary HD.  So I used the gparted live CD and copied by Ubuntu partition onto my new drive and expanded the partition.  My troubles started when I went to re-install grub.  When I booted from the live cd, grub showed by SATA drive as hd2 (logically, as I have two PATA drives with linux on hd1).  Re-boot, partition not found.  I was eventually able to install grub on the SATA drive, and get to a grub prompt.  Grub then decided that my SATA drive was hd0.  It set it up and got my system back up.  Now I want to restore my XP dual boot, which was previously on hd0, but I have no idea where it is now.  According to grub once I am fully booted, hd0 is my XP drive, but I know that it isn't, since my menu.lst has me boot into ubuntu on hd0.  

Has anyone else run into this?  Any suggestions??

Some useful info:

```
ryan@amd3000:/dev/disk/by-uuid$ ls -lh
total 0
lrwxrwxrwx 1 root root 10 2006-12-23 15:33 14BB5D3347699996 -> ../../sda3
lrwxrwxrwx 1 root root 10 2006-12-23 15:33 4510-5AB1 -> ../../hdb1
lrwxrwxrwx 1 root root 10 2006-12-23 20:33 458C-7F8D -> ../../sda4
lrwxrwxrwx 1 root root 10 2006-12-23 15:33 57f7b5f0-d051-4dfa-b84c-5af523a4d6cb -> ../../hdb2
lrwxrwxrwx 1 root root 10 2006-12-23 15:33 7fa72b1a-917d-4910-8de5-973f4f081171 -> ../../sda1
lrwxrwxrwx 1 root root 10 2006-12-23 20:33 9AFCEC1DFCEBF205 -> ../../hda2
lrwxrwxrwx 1 root root 10 2006-12-23 15:33 b395dfc7-82e3-479e-96ff-0b78888b037b -> ../../sda2
lrwxrwxrwx 1 root root 10 2006-12-23 20:33 C2941AD2941AC935 -> ../../hda1

```

```
ryan@amd3000:/boot/grub$ cat device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb

```

```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=b395dfc7-82e3-479e-96ff-0b78888b037b ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot
```

---

### Post by Ecthelion on 2006-12-29
I also have a Sata drive and the troubles I have had with it where because it wasn't marked as the first boot device in my bios.
So my advice is to check your **bios** and try to reinstall grub.

> Grub then decided that my SATA drive was hd0. It set it up and got my system back up. Now I want to restore my XP dual boot, which was previously on hd0, but I have no idea where it is now. According to grub once I am fully booted, hd0 is my XP drive, but I know that it isn't, since my menu.lst has me boot into ubuntu on hd0.

My window entry in grub looks like this:
> title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
So if my guess is right, that 'map' thing switches the name of the drives...

---

### Post by rpkehoe on 2006-12-29
I do have the SATA drive as my primary boot device in the BIOS.  I have made it a moot point my dumping XP completely, but I still don't understand the grub names.  It just doesn't make sense that grub would call the drives one thing while it boots, and then another once the system is up.

But it works, thats the important thing at this point.

---

### Post by cotcot on 2006-12-29
I solved a comparable problem by installing lilo.

---

