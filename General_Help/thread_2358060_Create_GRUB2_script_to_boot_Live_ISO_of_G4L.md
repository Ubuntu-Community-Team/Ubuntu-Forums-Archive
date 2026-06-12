---
title: "Create GRUB2 script to boot Live ISO of G4L"
date: 2017-04-09
forum: General Help
---

### Post by gtpt on 2017-04-09
Hi,

I downloaded the G4L iso file (g4l-v0.30.iso) from [https://sourceforge.net/projects/g4l/](https://sourceforge.net/projects/g4l/) .
This is s bootable disc of  G4L that is a hard disk and partition imaging and cloning tool.

I want to mount this iso somewhere on the file system and add a GRUB2 entry that allows me to boot G4L. 

My fdisk -l shows:
```
Dispositivo Inicializar     Start       Fim   Setores  Size Id Tipo
/dev/sda1   *                  63 209717247 209717185  100G  7 HPFS/NTFS/exFAT
/dev/sda2               209719294 312580095 102860802   49G  5 Estendida
/dev/sda5               308316160 312580095   4263936    2G 82 Linux swap / Sola
/dev/sda6               209719296 308316159  98596864   47G 83 Linux

Partition table entries are not in disk order.
```

Where an how do i place the iso content?
What script can i add to the /etc/grub.d folder in order to add this entry to the grub menu?

Thanks

---

### Post by yancek on 2017-04-09
Grub2 is capable of booting an iso file directly if the iso file is bootable this way.  Don't know if G4L is.  If it is, it doesn't matter whether it is on a Linux or windows partition.  If it is not bootable as an iso, then you would have to extract the files from the iso by loop mounting and copy them all to one of the partitions and add an entry in the grub.cfg file.  You would need to loop mount the iso file and take a look at whatever boot files it has to know what to use as an entry.

---

### Post by oldfred on 2017-04-09
Many examples here, if it is bootable.
 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847) 

I find getting boot options and path correct are often the major issues. 
Path has to be as seen before any system is mounted or as if from live installer, not from your install once booted.
And I often have to open ISO and look at its own boot parameters or options to see details if not identical to one we know.

---

