---
title: "Dual Boot - Unable to boot back to XP"
date: 2008-06-27
forum: General Help
---

### Post by Tonyr63 on 2008-06-27
Hi

I installed xunbuntu 8.04 to a new partition created during the install by manually resizing free space and initially following the install it restarted back to XP as if the install did not happen. I repeated the install a second time and I got a boot munu allowing me to boot into Windows and Xunbuntu.

However following an upgrade of the the Kernal from to 2.6.24.16 to 18 I do not seem to be able to boot into Windows any more. I still get the boot menu with the extra 2 lines for 2.6.24.18 but if I choose the xp option I get Starting ... GRUB and it hangs. It is like something has altered the boot.ini file or the Lunux equililent. The Kernal was upgrade on advice from live updates and seems to work OK.

Some background on the environment:

These are the relevant sections of the Menu.lst and the Menu.lst~ files.

menu.lst

title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=00268405-12ec-4972-80b2-ed392dc20e6c ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=00268405-12ec-4972-80b2-ed392dc20e6c ro single
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=00268405-12ec-4972-80b2-ed392dc20e6c ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=00268405-12ec-4972-80b2-ed392dc20e6c ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1

Menu.lst~

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=00268405-12ec-4972-80b2-ed392dc20e6c ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=00268405-12ec-4972-80b2-ed392dc20e6c ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1

The partition environment is:
Partition information:

sudo blkid

/dev/sda1: LABEL="ANNS DATA" UUID="1ECD-2877" TYPE="vfat"
/dev/sdb1: LABEL="DSK_1_1" UUID="B9B9-3C80" TYPE="vfat"
/dev/sdb5: TYPE="swap" UUID="a866c23b-4f66-4d5e-aad8-41f358f74d7c"
/dev/sdb6: UUID="00268405-12ec-4972-80b2-ed392dc20e6c" TYPE="ext2"

ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 120 2008-06-18 05:04 .
drwxr-xr-x 6 root root 120 2008-06-18 05:04 ..
lrwxrwxrwx 1 root root 10 2008-06-18 05:04 00268405-12ec-4972-80b2-ed392dc20e6c -> ../../sdb6
lrwxrwxrwx 1 root root 10 2008-06-18 05:04 1ECD-2877 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-18 05:04 a866c23b-4f66-4d5e-aad8-41f358f74d7c -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-06-18 05:04 B9B9-3C80 -> ../../sdb1



How should I edit the boot file so that I can access the Windows partition again?  I think I need to change the windows settinf to: title Windows NT/2000/XP root (hd0,1)

How do I edit this file as even logged in administrator through the GUI text editor it says I do not have permission to save changes?

MAny Thanks:)

---

### Post by WRDN on 2008-06-27
I'll try to give more advice later as Im going out in a minute, but to edit the file use the command:

```
sudo gedit /boot/grub/menu.lst
```

This will give you root priviledges and allow you to edit the file.

Also, please could you post the output of the following command

```
fdisk -l
``` 

*Note: thats the letter L, not a number 1*

---

### Post by drs305 on 2008-06-27
From what I read, you were able to access both linux and windows normally AFTER the repartition but not after updating the kernel? Installing a new kernel shouldn't have changed any partition information so the windows address should not have changed.

> **Tonyr63 said:**
> 
How should I edit the boot file so that I can access the Windows partition again?  I think I need to change the windows settinf to: title Windows NT/2000/XP root (hd0,1)

Remember that grub looks at partitions in a slightly different way. The first partition on the first drive is (hd0,0). The second partition on the first drive is (hd0,1), etc. The first partition on the second drive is (hd1,0), etc. (You basically subtract 1 from each drive and partition number.)

Do you know which partition your windows is on? If not, posting the info from WDRN's request should tell us.

First make sure grub is current:
```
sudo update-grub
```

Install StartUp-Manager. It's a gui app that edits menu.lst and helps prevent errors commonly made by manually editing menu.lst.

Install:
```
sudo aptitude install startupmanager
```

To run:
System, Administration, StartUp-Manager

Go to the first tab and select Default Operating System: Windows just to see if that will restore the correct settings.

For more on StartUp-Manager:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

