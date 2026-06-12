---
title: "windows partition problem"
date: 2007-12-01
forum: General Help
---

### Post by Isleromanolete on 2007-12-01
Hello everybody I've been using Ubuntu for a little while and have 6.06 LTS (missed out on the updates and now i cant update directly):( if anyone wants to help me in tht subject theyre welcome to also.

Anyway, the reason why ive written is that my windows xp proffesional partition is screwed up and i tried researching some things to fix it but no success really. Here is the fdisk -l and the grub menu list respectively

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6167    49536396    7  HPFS/NTFS
/dev/hda2            6168        7245     8659035   83  Linux
/dev/hda3            7246        7296      409657+   5  Extended
/dev/hda5            7246        7296      409626   82  Linux swap / Solaris




## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.15-23-server
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-server root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-server
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-server (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-server root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-server
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1



as you can see it is all on one hard drive and windows is the first partiontion. I need help becuase when i select windows on grub it gives me the 

file type unknown 0 x 7 thing


any help woulb be wonderful thank you

---

### Post by bingoUV on 2007-12-01
install ntfsprogs. Unmount the partition. Then run ntfsfix on the partition. It might help, though it is not full NTFS checker.
```

sudo apt-get install ntfsprogs
sudo umount /dev/sda1
sudo ntfsfix /dev/sda1

```

---

