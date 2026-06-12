---
title: "Grub is gone?!"
date: 2008-06-30
forum: General Help
---

### Post by blackaardvark on 2008-06-30
Hi guys,

I'm using 7.10 and after updating with synaptic recently my grub menu has disappeared.  I usually have ubuntu and xp but it now boots straight to ubuntu.  Do I have to reinstall grub or can I just restore it somehow?  I've tried using Super Grub Disc but I get an error 28???

I've tried using gparted but it doesn't detect the partitions on the disc :confused: so I can't change the boot flag easily.



Thanks in advance.

---

### Post by ibutho on 2008-06-30
If you look at the file /boot/grub/menu.lst is Windows listed? If it is, can you post its entry. Also post the output of running Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by nnamdi on 2008-06-30
you recover it back wit ur live cd, boot with the cd then open terminal and type this there

```

sudo grub

find /boot/grub/stage1

root (hd ??)

setup(hd0)

quit


```

---

### Post by blackaardvark on 2008-06-30
> **nnamdi said:**
> you recover it back wit ur live cd, boot with the cd then open terminal and type this there

```

sudo grub

find /boot/grub/stage1

root (hd ??)

setup(hd0)

quit


```

I've tried that and I get it failing at the last step with an error 12 (i think..)

The windows entry for my menu.lst is:
```
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

and fdisk -l gives me:
```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9       10494    84222716+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           10495       29787   154971022+   5  Extended
/dev/sda4           20062       29787    78124095    b  W95 FAT32
/dev/sda5           10495       19682    73802547   83  Linux
/dev/sda6           19683       20060     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a06291b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706    7  HPFS/NTFS

```


Hope that helps!

---

### Post by caljohnsmith on 2008-06-30
I had a problem going from Gutsy to Hardy where my Grub system files were not properly updated. It sounds like your situation is exactly like mine, so I would recommend booting into Ubuntu and doing the following commmand:
```
sudo grub-install /dev/sda --recheck
```
That will reinstall grub to the MBR of your HDD and make it point to your Ubuntu partition for the menu.lst and all the other grub files. 

Using nnamdi's method will normally work if you don't need to reinstall grub's configuration files (stage1, stage2, etc), but I think your situation is like mine and you probably need to update your grub system files as well as fix your MBR.

---

### Post by blackaardvark on 2008-06-30
I'm getting this:
```

~$ sudo grub-install /dev/sda --recheck
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.

```

Eeek??

I might mention that when I search for the grub root I get (hd0,5)....

---

### Post by caljohnsmith on 2008-06-30
> **blackaardvark said:**
> I'm getting this:
```

~$ sudo grub-install /dev/sda --recheck
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.

```

Eeek??

I might mention that when I search for the grub root I get (hd0,5)....
If Grub is not reading the stage1 file correctly, sounds like you may need to reinstall Grub. Before you do that, be sure to back up your menu.lst file to your home directory or somewhere it can't be harmed when you reinstall grub.

But before you reinstall Grub, I would try deleting all the files in /boot/grub manually, except menu.lst, and then run that grub-reinstall command again. That's exactly what I did on my computer to fix my problem, and then the grub-install command regenerated all the necessary stage1, stage2, etc. files in the /boot/grub directory and I was good to go. That might be all you need.

---

### Post by blackaardvark on 2008-06-30
Ah well, that didn't work.  I guess I'll just have to reinstall it.

Thanks to everyone who tried :D

---

