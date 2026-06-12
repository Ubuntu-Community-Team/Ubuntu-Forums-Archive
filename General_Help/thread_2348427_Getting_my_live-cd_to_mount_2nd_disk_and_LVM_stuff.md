---
title: "Getting my live-cd to mount 2nd disk and LVM stuff"
date: 2017-01-03
forum: General Help
---

### Post by David_Partridge on 2017-01-03
My live-cd is now working pretty well, but while it mounted the SCSI raid regular partitions at /dev/sda1, it didn't do anything with the regular partition on the SATA SSD which was assigned /dev/sdb or with the LVM stuff on the SSD.

Hmmm Ubuntu has been very inconsistent over which of these it assigns as /dev/sda and which /dev/sdb.  I *thought* there were precedence rules for this?

What do I need to do to get it to handle these?

Thanks
Dave

---

### Post by David_Partridge on 2017-01-04
Well, guess what: This was also a case of adding another kernel module to  etc/initramfs-tools/modules in the cd build work rootfs area.

When running the chroot part of the install, part of the procedure is to run [FONT=courier new]update-initramfs -u -k $(uname -r)[/FONT] to build the initrd.img.

Unfortunately dm-mod.ko isn't a default part of the 4.8.13 kernel (and I  think also not part of the 4.4.0 kernels), so I had to change file  /shared/livecd/work/rootfs/etc/initramfs-tools/modules so that it would  include dm-mod into the initramfs:[FONT=courier new]

[/FONT]```
[FONT=courier new]# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
overlay
dm-mod
[/FONT]
``` 

Once that was done, I re-ran the update-initramfs under the chroot and rebuilt the image.

Now I could see my LVM stuff!

Dave

---

### Post by kyknos12 on 2017-01-04
To be able to see LVM parts I think so if I'm not mistaken from terminal sudo vgchange -a y

---

