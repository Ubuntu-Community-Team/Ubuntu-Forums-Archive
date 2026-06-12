---
title: "GRUB edit"
date: 2008-01-26
forum: General Help
---

### Post by mschraier on 2008-01-26
I currently am running XP, Ubuntu & Kubuntu.  I will remove the Kubuntu partition to make that space available.  Here is menu.lst.  The first boot is for Kubuntu.  What do I need to remove so that I only have XP & Ubuntu?  I waas only able to see this version of GRUB while in Kubuntu. When I ran gedit in Ubuntu, only it and XP were in the bootloader.  Will just removing the partition do it or do I need to edit grub in KATE first and boot LIVE to remove the partition??

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e2a29d31-b9b9-4806-9e4f-3c2bff1f6ec9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e2a29d31-b9b9-4806-9e4f-3c2bff1f6ec9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9c48ce3a-e2e2-4f57-b266-e2884aae1fc3 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9c48ce3a-e2e2-4f57-b266-e2884aae1fc3 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by taurus on 2008-01-26
Which partition is your Kubuntu, /dev/sda2 or /dev/sda4?

---

### Post by mschraier on 2008-01-26
sd1 - XP
sd2 - ubuntu
sd4 - kubuntu
sd3 - swap space

i want to remove kubuntu and make grub reflect only sd1 & sd2 for boot.  sd4 can be removed via gparted on a livecd unless there is a way to do it while in ubuntu.

---

### Post by taurus on 2008-01-26
Did you install GRUB to MBR under Kubuntu or Ubuntu?

If you want to remove /dev/sda4, Kubuntu, make sure it's not mount and you can use gparted to format it, converting it to ext3 partition so you can use it as a storage in Ubuntu.  Otherwise, format it to vfat or ntfs if you want to share that space with windows.

---

### Post by mschraier on 2008-01-27
I honestly dont know where I installed GRUB to.  I think I re-write the MBR, but not positive.  What needs to be edited so that its only sd1 & sd2 booting?????

---

