---
title: "GRUB - ubuntu - problem booting Windows XP"
date: 2006-07-21
forum: General Help
---

### Post by Mirko Scurk on 2006-07-21
Hi!

I have been using Ubuntu from its appearance. I have never had problems with GRUB until few days back. I can not recall if grub was upgraded but it unexpectedly ceases to boot Windows XP. I didn't make any BIOS, HW or substantial SW change lately.

Configuration is:

AthlonXP 2500+ on ASUS A7N8X Deluxe MBO 1GB RAM

BIOS boot order:

CD
HD0

Disk configuration:
IDE first channel master 80GB PATA
IDE second channel master DVD-RW
IDE second channel slave DVD-ROM
SATA 400GB

80GB PATA (hd0):

/dev/hda1	swap
/dev/hda3	ext3 ubuntu root
/dev/hda4	ext3 ubuntu home
/dev/hda5	ext3 fedora boot
/dev/hda6	lvm fedora 

400GB SATA (hd1):

/dev/sda1	NTFS WinXP boot
/dev/sda2	NTFS 
/dev/sda3	NTFS 
/dev/sda4	FAT32 

GRUB: grub 0.97-1ubuntu9

Device.map:
(fd0)	/dev/fd0
(hd0)	/dev/hda
(hd1)	/dev/sda

menu.lst:
default		0
timeout	4

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

title		Fedora Core 5
root		(hd0,4)
chainloader	+1

When booting XP I get error message and system freezes:

Booting "Microsoft Windows XP Professional"
root (hd1,0)
Filesystem type unknown, partition type 0x7.
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

When I change BIOS boot order to 

CD
SCSI/SATA

I am able to boot windows properly but normally there is no sign of GRUB as it has been installed on /dev/hda MBR.

I tried with rootnoverify (hd1,0) but had no luck. I'm able to mount ntfs partitions from ubuntu with no problem.

Help please!

---

### Post by Harold P on 2006-07-21
> **Mirko Scurk said:**
> Hi!

I have been using Ubuntu from its appearance. I have never had problems with GRUB until few days back. I can not recall if grub was upgraded but it unexpectedly ceases to boot Windows XP. I didn't make any BIOS, HW or substantial SW change lately.

Configuration is:

AthlonXP 2500+ on ASUS A7N8X Deluxe MBO 1GB RAM

BIOS boot order:

CD
HD0

Disk configuration:
IDE first channel master 80GB PATA
IDE second channel master DVD-RW
IDE second channel slave DVD-ROM
SATA 400GB

80GB PATA (hd0):

/dev/hda1    swap
/dev/hda3    ext3 ubuntu root
/dev/hda4    ext3 ubuntu home
/dev/hda5    ext3 fedora boot
/dev/hda6    lvm fedora 

400GB SATA (hd1):

/dev/sda1    NTFS WinXP boot
/dev/sda2    NTFS 
/dev/sda3    NTFS 
/dev/sda4    FAT32 

GRUB: grub 0.97-1ubuntu9

Device.map:
(fd0)    /dev/fd0
(hd0)    /dev/hda
(hd1)    /dev/sda

menu.lst:
default        0
timeout    4

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title        Ubuntu, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin 
boot

title        Other operating systems:
root
[I]
title        Microsoft Windows XP Professional
**root**        (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader    +1[/I]

title        Fedora Core 5
root        (hd0,4)
chainloader    +1

When booting XP I get error message and system freezes:

Booting "Microsoft Windows XP Professional"
root (hd1,0)
Filesystem type unknown, partition type 0x7.
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader    +1

When I change BIOS boot order to 

CD
SCSI/SATA

I am able to boot windows properly but normally there is no sign of GRUB as it has been installed on /dev/hda MBR.

I tried with rootnoverify (hd1,0) but had no luck. I'm able to mount ntfs partitions from ubuntu with no problem.

Help please!
According to [this]("https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/10661"), it looks like that root I have bolded is supposed to be rootnoverify, or it could be something else. I hope that link helps. ;)

---

### Post by Mirko Scurk on 2006-07-21
Saw that link before and tried that as I stated at the end of my post. I suspect that there is some problem with different disc geometry in win and grub but I'm not sure how to check and fix that.

Thanks anyway!

---

### Post by Mirko Scurk on 2006-07-21
Any experts for grub around?

---

### Post by Mirko Scurk on 2006-07-23
Well, just partial solution but I can boot everything again!

> **Mirko Scurk said:**
> Hi!


BIOS boot order:

CD
HD0

Disk configuration:
IDE first channel master 80GB PATA
IDE second channel master DVD-RW
IDE second channel slave DVD-ROM
SATA 400GB

80GB PATA (hd0):

/dev/hda1	swap
/dev/hda3	ext3 ubuntu root
/dev/hda4	ext3 ubuntu home
/dev/hda5	ext3 fedora boot
/dev/hda6	lvm fedora 

400GB SATA (hd1):

/dev/sda1	NTFS WinXP boot
/dev/sda2	NTFS 
/dev/sda3	NTFS 
/dev/sda4	FAT32 

GRUB: grub 0.97-1ubuntu9

Device.map:
(fd0)	/dev/fd0
(hd0)	/dev/hda
(hd1)	/dev/sda



Despite I didn't want to write anything to Win (SATA) disk I had to give up from that configuration. I just installed grub on /dev/sda an changed menu.lst a little and everything is working again!


Old menu.lst
> **Mirko Scurk said:**
> 

menu.lst:
default		0
timeout	4

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

title		Fedora Core 5
root		(hd0,4)
chainloader	+1



New menu.lst:
default		0
timeout	4

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin 
boot

title		Other operating systems:
root

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


title		Fedora Core 5
root		(hd1,4)
savedefault
chainloader	+1


It seems that grub changed in a way that one must set in BIOS, device that Windows was originaly installed on, as boot device. I changed BIOS boot order to:
CD
SCSI

Interestingly, device.map stayed same as before:

root# grub-install --recheck /dev/sda
(fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/sda

Note discrepancy between device.map and menu.lst!!!

Grub is here very inconsistent and on such cases you can see true weaknesses of open source development model. It is probably lack of communication between various developers. 

More strange, everything worked pefectlly on same hardware for over two years just until week ago!

---

