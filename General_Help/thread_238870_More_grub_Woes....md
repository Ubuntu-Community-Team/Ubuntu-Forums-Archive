---
title: "More grub Woes..."
date: 2006-08-18
forum: General Help
---

### Post by chadwick359 on 2006-08-18
Okay, Grub is getting me to the point of considering switching to Lilo.](*,)  I managed to convince it to not hate me after inserting a harddrive on my new PCI IDE card, and for a few reboots, it was good. But now, every time I try to select either of the harddrives that have windows installed, (hd1 and hd2) Grub displays the boot paramaters, thinks for just a moment, and spits out a bunch of garbage at me. (including the old dos smileyface) Anybody have any suggestions on this?

---

### Post by bernied on 2006-08-18
You will need to be a little more specific about your particular problem before anyone can help you. It sounds like you are trying to boot multiple versions of Windows on more than one disk, not something that (selfish) Windows is known to do well. Are you sure the problem is with grub and not with the Windows bootloader that you are probably chainloading to?

Please post the output from these:

# fdisk -l
(And it might be useful if you annotate this - describe what each of the partitions is for and what filesystem is on each. And tell us whether the list looks 'right'. Is all of your disk space accounted for?)

# cat /boot/grub/menu.lst

Also say whether you are using any of SATA, RAID or LVM.

---

### Post by chadwick359 on 2006-08-18
Sorry, I thought I would be able to edit this before anybody got to reply, but things got heavy at work. fdisk -l outputs 

```
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         653     5245191   83  Linux
/dev/hdb2             654         914     2096482+  82  Linux swap / Solaris
/dev/hdb3             915        2434    12209400   83  Linux

[CODE]Disk /dev/hdf: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1       10010    80405293+   7  HPFS/NTFS

```

Hda is my windows Xp install, Hdb is Ubuntu, and Hdf is windows 2000, which is on a IDE PCI controller card. I had some issues getting grub to load properly after installing that card, because of the way that grub insists on numbering the drives. Hda->hd1 Hdb->hd0 Hdf->hd2. Here's my menu.lst.

```
title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.15-26-686
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```

It should be noted, I don't need to be able to boot to 2k, i just tried switching up the harddrive listing for the last entry to see if it would boot. Unfortunately it gives me the same stream of gibberish that XP's drive does.

---

### Post by TripleE on 2006-08-18
I may be wrong, but you may need to fix your windows boot loader first:

boot to the windows CD
go to recovery console
do a "fixboot"
then a "fixmbr"
re-install grub

---

### Post by chadwick359 on 2006-08-18
Bah, I was worried about that being the only solution. Well, thanks.

---

### Post by bernied on 2006-08-19
I think you should try using the map command in your Windows entries. My understanding is that this tells windows that it is on the first disk, which it likes. Try this:
```
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
# makeactive 
chainloader     +1
```

And you should not need the makeactive command, because this manipulates the boot flag on a partition (not the disk), and this flag is already set on this partition (indicated by the asterix on the fdisk entry).

For your W2000 entry, try a similar entry, but use hd2 instead of hd1.

You might also want to check your jumpers on the disk drives, or see if there are any settings in BIOS for saying which disk is which. It's curious that grub changes their order. If you did fix this though, you'd have to rejig your grub again.

One of your Ubuntu entries (Ubuntu, kernel 2.6.15-23-386) is different to the rest, with root set to hd1.

---

