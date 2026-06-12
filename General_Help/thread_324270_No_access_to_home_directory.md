---
title: "No access to home directory"
date: 2006-12-23
forum: General Help
---

### Post by phstpok on 2006-12-23
Ubuntu6.10 clean install with hda1-swap, hda3=/, hda4=/home. I have a spare partition hda2, on which I installed Dreamlinux. 

I did not want Dreamlinux as my default os, so changed /boot/grub/menu.lst in Dreamlinux to have Ubuntu as default. After this, boot would hang part way through booting Ubuntu, with no error messages, just frozen screen.

I booted the Ubuntu live cd, mounted hda3, then ran grub, root (hd0) This looked okay, but when I booted, I got an error on not recognising  UUID=18916bab-33d7-4614-91df-b0308979a5b5, boot failed with error 8, leaving me at a root prompt. I commented out the UUID line in /etc/fstab, which is the dreamlinux installation on hda2. Rebooting gets me to the Ubuntu login page, but when I log in, I get another error message: 

"$HOME/.dmrc is being ignored.This prevents the default session from being saved. File should be owned by user and have 644 permissions. User $HOME dir must be owned by user and not writable by others." 

It then boots into the gui but I cannot access anything in my home directory, none of my startup script are run, no themes etc. I have checked permissions, user & groups etc. At a loss here.

/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=3aaacb2d-737b-40fe-a26a-5a0a4b9164fb /               ext3    defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0       1
# /dev/hda4
UUID=2364a5a6-989a-4940-a950-5eb75a6501e1 /home           ext3    defaults        0       2
# /dev/hda2
# UUID=18916bab-33d7-4614-91df-b0308979a5b5 /media/hda2     ext3    defaults        0       2
# /dev/hda1
UUID=a01f800f-b21f-47e5-a871-d637d0be5c64 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Ubuntu /boot/grub/menu.lst (misc instructions & comments edited out)

Default		0

timeout		10

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Sabayon Linux i686 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/kernel-genkernel-x86-2.6.18-gentoo dolvm2 root=/dev/ram0 ramdisk=8192 real_root=/dev/hda2 splash=silent,theme:default quiet CONSOLE=/dev/tty1 init=/linuxrc doslowusb vga=791 
initrd		/boot/initramfs-genkernel-x86-2.6.18-gentoo
savedefault
boot

---

