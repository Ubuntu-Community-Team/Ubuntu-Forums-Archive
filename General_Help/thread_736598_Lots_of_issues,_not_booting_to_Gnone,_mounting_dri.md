---
title: "Lots of issues, not booting to Gnone, mounting drives, etc"
date: 2008-03-26
forum: General Help
---

### Post by aroth87 on 2008-03-26
Ok, so this is like the third thread I've started in three days and I'm really sorry about that.

Here's the scoop on how all of my problems started. I had a perfectly good Ubuntu install working on my new laptop. I decided to use some of the unused space on the hard drive to try out Debian. So I installed Debian and decided I didn't like it and formatted the partition. This made GRUB throw fits since the Debian install had changed where GRUB was installed. I got the GRUB issue fixed and am able to boot my Ubuntu install again.

However, whenever I select Ubuntu in GRUB, it starts to load but instead of starting up Gnome, it takes me to command prompt. If I type 'reboot' at the prompt and hit 'Enter' Gnome will start up.

Once in Gnome, my other partitions that used to be mounted automatically no longer are. I can mount them, using 'sudo mount /media/sda3' and then cd into them and see that all the files are still there, but it doesn't show up on my desktop.

Finally, I have conky set up to show the amount of swap being used. Ever since I installed/uninstalled Debian, It shows "NoSwap".

Can anyone help me get things back in order? I'd like to start by booting straight into Gnome instead of a command prompt. Then move to maybe getting the swap issue fixed. And finally, I'd really like the drive /media/sda3 to mount automatically and be available on my desktop, like it was before.

Adam

---

### Post by drzoo2 on 2008-03-26
Are you sure your not booting into recovery mode. You should post your grub config for help.

Here's mine
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f5ccb51e-5838-46a4-8aae-f5d2c1d24a74 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f5ccb51e-5838-46a4-8aae-f5d2c1d24a74 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

Also your fstab and partition table

---

### Post by aroth87 on 2008-03-26
menu.lst:
```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f8879e0-7242-4a44-969a-9ae9d562643f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f8879e0-7242-4a44-969a-9ae9d562643f ro single
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Linux (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/sda2 vga=0x314 resume=/dev/sda1 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Failsafe (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/sda2 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd
savedefault
boot

```

fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8f8879e0-7242-4a44-969a-9ae9d562643f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=9655db90-99ef-4173-b977-57d55fad1626 /media/sda2     ext3    defaults        0       2
#/dev/sda3
UUID=a58eb376-e370-45a0-bf8e-d9838986e9e3 /media/sda3     ext3    defaults        0       2
#/dev/sda1
UUID=26f3c231-5fba-44ae-8873-c07b9528a502 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

partition table:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00031b39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1247        1730     3887730   82  Linux swap / Solaris
/dev/sda2               1        1246    10008463+  83  Linux
/dev/sda3            1731       18242   132632640   83  Linux
/dev/sda4   *       18243       19457     9759487+  83  Linux

Partition table entries are not in disk order

```

I was wanting to get rid of the part in the menu.lst about Debian, but I wasn't sure how much of it I could take out and what needed to be left. Would it be ok to take out everything after "### END DEBIAN AUTOMAGIC KERNELS LIST"?

Conversely, would it be far easier for me to just reinstall Ubuntu? I've only had it set up for about a week so it wouldn't be much effort for me to set everything back up after a fresh install.

Adam

---

### Post by aroth87 on 2008-03-26
Disregard this thread, I just reinstalled Gutsy.

Adam

---

