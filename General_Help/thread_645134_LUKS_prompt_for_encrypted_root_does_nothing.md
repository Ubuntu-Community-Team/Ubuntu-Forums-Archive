---
title: "LUKS prompt for encrypted root does nothing"
date: 2007-12-19
forum: General Help
---

### Post by onyxrev on 2007-12-19
I've been trying to get my Macbook's Feisty install working with an encrypted root partition using LUKS.  I'm really close as I am greeted with the "Enter LUKS passphrase:" prompt upon booting.  But, I seem unable to type anything in at this point.  If I enter in my password (which isn't echoed back, obviously) and then hit enter, it's as if I entered nothing at all.  There's no error or confirmation of a passphrase attempt.  Up until this point I had been running an encrypted home and unencrypted root and that LUKS prompt worked fine.

I have cross-referenced my configuration files with the more recent guides and I am quite certain that everything seems to be set up correctly.  It seems like it must be a grub or very basic problem because it never gets to the point where it would have access to fstab or crypttab.

Anyone have any thoughts?

GRUB:

> title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,6)
kernel		/vmlinuz-2.6.20-16-generic root=/dev/mapper/croot ro nosplash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

fstab:

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
/dev/mapper/croot       /       ext3    defaults,errors=remount-ro 0 1
# /dev/sda5
/dev/sda7               /boot   ext3    defaults        0       2
/dev/mapper/cswap       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda6 /media/storage hfsplus rw,exec,auto,users 0 0
/dev/mapper/cryptohome  /home   ext3    nodev,nosuid 0 2
/dev/sda2 /media/MacintoshHD hfsplus user,ro 0 0

crypttab:

> # <target name> <source device>         <key file>      <options>
croot           /dev/sda3               none            luks
cswap           /dev/sda4         /dev/random   swap
cryptohome      /dev/sda5       none    luks,check=ext2,retry=3

---

