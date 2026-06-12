---
title: "Boot failure at pivot_root"
date: 2005-10-20
forum: General Help
---

### Post by jcspray on 2005-10-20
Hello,

My situation is as follows: the computer has two hard drives, hdb and
sda.  It's running off hdb right now, but ultimately the goal is to use
only sda.

On hdb9 there is a working breezy install, with a custom-compiled kernel
which was needed in order to talk to sda.  sda5 contains an ext3
filesystem containing everything from hdb9, copied using ```
find . -xdev
-print | cpio -padm /mnt
```

I try to boot from sda5 with GRUB using:```

root (hd0,4)
kernel /boot/vmlinuz-2.6.14-rc4 root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.14-rc4
boot
```

This works up until the point where init tries to start, whereupon it
gives the error:```

pivot_root: no such file or directory
/sbin/init: 428: cannot open /dev/console
```

pivot_root is apparently like a souped-up chroot, used in the ubuntu
boot process for remounting the root filesystem.

My googling returned two possible causes:
      * The /initrd directory that's used by pivot_root does not exist.
        But it's right there staring at me on /dev/sda5
      * The initrd image does not contain the correct modules to mount
        this filesystem.  My initrd contains sata_sis (sata driver for
        this controller), libata, scsi_mod, sr_mod - that should be
        everything I need, surely?  Anyway, shouldn't the kernel have
        panicked and said it couldn't mount the root filesystem in this
        case?

I am stumped.  Appreciations suggested.

---

### Post by KnottyMan on 2005-10-20
Had similiar problem booting a DAC960 raid.  I have since solved my problem...

Can you install directly onto the sata drive?  It will be easier if you can.

How I fixed my DAC960:

First I was able to install directly onto the RAID volume
before clicking continue at the end, ALT-F2 to get to a console.
cd /target
chroot /target
vi /etc/mkinitramfs/modules
add "DAC960"  (case sensitive matters kids) or whatever module you need
save
cd /boot
mkinitramfs -o initrd-dac960
edit grub's menu.lst to use the new initrd

reboot and should work now.

If you cannot install direct onto sata drive, there is a way.  I had to do this to make my areca sata raid work.

install onto IDE/something that works.  Compile kernel/do whatever you have to to get a kernel module that works.  Copy the module to floppy/flash.

remove IDE drive and install sata drive.  Boot CD to install ubuntu.  Continue till you get to a good stopping point, usually when it asks about networking.  ALT-F2 to console.  Mount floppy, modprobe kernel module.  ALT-F1 and continue install.  

At this point ubuntu should be able to install right onto the sata drive.  Do this and continue till the end until it asks to reboot.

ALT-F2 and cp the kernel module from the floppy to  /target/lib/modules/[kernel version]/driver/scsi.  cd /target, chroot /target and follow my above directions for a new initrd.  

That should do it.

---

