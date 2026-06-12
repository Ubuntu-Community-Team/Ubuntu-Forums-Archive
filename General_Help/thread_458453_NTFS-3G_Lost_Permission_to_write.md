---
title: "NTFS-3G Lost Permission to write"
date: 2007-05-29
forum: General Help
---

### Post by sonojo on 2007-05-29
I installed Kurumin Linux based on Debian with ntfs-3g support with 5 ntfs partition with sucess to read and write. After I booted on windows and came back to Linux the partition sdb5 is not writing any more, I can only read it, and the others I can still read and write. What I find strange is that when I edit as root the fstab to: /dev/sdb5	/mnt/sdb5	ntfs-3g silent,locale=pt_BR.iso88591,umask=0 0 0    and reboot to linux it comes back to: /dev/sdb5	/mnt/sdb5	ntfs	noauto,users,exec,ro,umask=000	.I don't know what to do anymore for when change the the fstab it does not change after rebooting. 

This is my fstab:

# /etc/fstab: static file system information
#
# <file system>	<mount point>	<type>	<options>	<dump> <pass>

# adicionado por kurumin	/dev/sda1
/dev/sda1	/	reiserfs	defaults	0 1
# adicionado por kurumin	/dev/sdb1
/dev/sdb1	/mnt/sdb1	ntfs-3g silent,locale=pt_BR.iso88591,umask=0 0 0
# adicionado por kurumin	/dev/sdb6
/dev/sdb6	/mnt/sdb6	ntfs-3g silent,locale=pt_BR.iso88591,umask=0 0 0
# adicionado por kurumin	/dev/sdb8
/dev/sdb8	/mnt/sdb8	ntfs-3g silent,locale=pt_BR.iso88591,umask=0 0 0
# adicionado por kurumin	/dev/sdb9
/dev/sdb9	/mnt/sdb9	ntfs-3g silent,locale=pt_BR.iso88591,umask=0 0 0

# adicionado por kurumin	/dev/sdb5
/dev/sdb5	/mnt/sdb5	ntfs	noauto,users,exec,ro,umask=000	0 0

# adicionado por kurumin	/dev/sdb7
/dev/sdb7	/mnt/sdb7	vfat	noauto,users,exec,umask=000,shortname=mixed,quiet	0 0

# adicionado por kurumin
/dev/cdrom	/media/cdrom	udf,iso9660	user,noauto	0 0

sys /sys sysfs noauto 0 0
/dev/pts /dev/pts devpts mode=0622 0 0
usbfs /proc/bus/usb usbfs defaults 0 0

---

