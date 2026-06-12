---
title: "Ghost"
date: 2007-02-03
forum: General Help
---

### Post by Angelaki on 2007-02-03
I have two HDD in my pc. HD=40GB and HDB=10GB. I have install Kubuntu 6.10 in HDB and work fine. Then i clone the HDB in HDA. Now i cant boot in HDA. I take an error 15. In HDB i can boot without prob. I need your help. 
 
[COLOR="Red"] My menu.lst [/COLOR]
 
 
 default 0
 timeout 10
 
 title Kubuntu (hda), kernel 2.6.15-26-386 (on /dev/hda1)
 root (hd0,0)
 kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash 
 initrd /boot/initrd.img-2.6.15-26-386
 savedefault
 boot
 
 
 ## ## End Default Options ##
 
 title Ubuntu, kernel 2.6.17-10-generic
 root (hd1,0)
 kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
 initrd /boot/initrd.img-2.6.17-10-generic
 quiet
 savedefault
 boot
 
 title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
 root (hd1,0)
 kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
 initrd /boot/initrd.img-2.6.17-10-generic
 boot
 
 title Ubuntu, memtest86+
 root (hd1,0)
 kernel /boot/memtest86+.bin
 quiet
 boot
 
 ### END DEBIAN AUTOMAGIC KERNELS LIST
 
 # This is a divider, added to separate the menu items below from the Debian
 # ones.
 title Other operating systems:
 root
 
 
[COLOR="red"] sudo fdisk -l[/COLOR]
 
 Disk /dev/hda: 40.0 GB, 40020664320 bytes
 255 heads, 63 sectors/track, 4865 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 
 Device Boot Start End Blocks Id System
 /dev/hda1 * 1 4801 38564001 83 Linux
 /dev/hda2 4802 4865 514080 82 Linux swap / Solaris
 
 Disk /dev/hdb: 10.2 GB, 10248118272 bytes
 255 heads, 63 sectors/track, 1245 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 
 Device Boot Start End Blocks Id System
 /dev/hdb1 * 1 1190 9558643+ 83 Linux
 /dev/hdb2 1191 1245 441787+ 82 Linux swap / Solaris



[COLOR="red"]I foolowing this instruction but the result is the same. ERROR 15[/COLOR]

root (hd0,0) 
setup (hd0) 
quit


Except this i have and a new problem. If i want to restart my pc and boot again in Kubuntu in HDB i must pull over the power cable for 5 sec and then to power on the PC. If i dont do it the PC halt in the first line in Kubuntu. 
 
 Maybe my pc has GHOST!!!!    :) :) 
 
 
 P.S. Please HELP ME!!   :(

---

### Post by feest on 2007-02-03
however you copies all the files to your new disk, it's not guaranteed it will boot. because hard drives do have such things as indexes that tell them where to boot. such indexes are generated at an install but not with direct copying

---

