---
title: "Ubuntu Feisty's Grub menu.lst"
date: 2007-04-19
forum: General Help
---

### Post by pepsi_max2k on 2007-04-19
Hi, can someone post feisty's default grub config please. 

I'm about to install it to a tripple boot system, but don't want to replace Suse's GRUB menu. Which is gonna mean I'll end up with an unbootable ubuntu install to start with, and have to add in a new option to grub's menu.lst on my Suse partition. So far it looks like this, if any one wants to edit it or give tips then feel free, but i should be able to work it out myself if i know what ubuntu uses by default (it should end up on hd0,3).

**EDIT:** While I'm here... Is there any way to kinda share a grub install between ubuntu and suse? Eg. being able to hit "restart > windows" in both of them and it doing so? I'm thinking something like symlinking the grub folder in ubuntu to the one in suse...

```
default 1
timeout 8
gfxmenu (hd0,2)/boot/message

title openSUSE 10.2
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.20.2-67-default root=/dev/hda3 vga=0x317 resume=/dev/hda2 splash=silent showopts
    initrd /boot/initrd-2.6.20.2-67-default

title Windows XP
    map (hd0) (hd1)
    map (hd1) (hd0)
    rootnoverify (hd1,0)
    chainloader +1
    makeactive

title Failsafe -- openSUSE 10.2
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.20.2-67-default root=/dev/hda3 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.20.2-67-default

title Turn Off
   savedefault 0
   cat /boot/grub/default
   halt
```

---

### Post by pepsi_max2k on 2007-04-20
bump, hopefully there's more around a day later :) soo... default grub menu.lst anyone?

---

### Post by pepsi_max2k on 2007-04-21
What I was looking for. I just got rid of the "savedefault" and used the main ubuntu entry in my previous grub install.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

default		0
timeout		10

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5fe00d95-904b-49d7-bfa4-aaba07e25918 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5fe00d95-904b-49d7-bfa4-aaba07e25918 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
```

---

