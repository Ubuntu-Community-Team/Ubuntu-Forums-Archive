---
title: "Errors on updating (Swap file config scrambled?) L18.04"
date: 2018-12-03
forum: General Help
---

### Post by df1234 on 2018-12-03
(Lubuntu 18.04.1 Installed on a SSD on a dual boot machine booting through GRUB menu)

When my system updates it produces errors i think because the swap file configuration is scrambled

[COLOR=#000080][FONT=fixedsys]W: initramfs-tools configuration sets RESUME=UUID=8690dd17-8c64-490e-9c50-d6099db9e1e4
W: but no matching swap device is available.[/FONT][/COLOR]

The UUID id the one in my /etc/initramfs-tools/conf.d/resume file

[COLOR=#ff0000][FONT=fixedsys]RESUME=UUID=8690dd17-8c64-490e-9c50-d6099db9e1e4[/FONT][/COLOR]

But this UUID does not appear on my system!
The Linux Filesystem is on UUID c1b34c8f-6ab6-460d-9da0-56b763da6438
The Swap Partition is on UUID 5bb862d2-c5fa-4dbb-bc23-e8f64bdc3e58
The latter appears to be the same (?) as the "Block Device" (/dev/mapper/cryptswap1) which is on UUID 8833e4b8-9f53-4ba2-94ec-200f32b23116

I presume that the resume file has got corrupted presumably by a previous update

Looking through the forums there is some indication that the /etc/fstab file is relevant; it reads:
[FONT=fixedsys]
[COLOR=#ff0000]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=c1b34c8f-6ab6-460d-9da0-56b763da6438 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=9ABD-D7B2  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdb6 during installation
#UUID=5bb862d2-c5fa-4dbb-bc23-e8f64bdc3e58 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
LABEL=DATA /mnt/DATA auto nosuid,nodev,nofail,x-gvfs-show 0 0[/COLOR][/FONT]

Questions:
1) Is the solution as simple as overwriting the details in "resume" with something else from fstab? If so with what?
2) Any idea how the problem may have occurred (I don't "fiddle" beneath the hood, so I suspect that this is an software update error)

The following may also be relevant 

1) There have been allied problems(?) on resuming from Suspend - which prompted me to file a bug report:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1795678](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1795678)

2) Booting is problematic; 
Hard rebooting causes a Kernel panic and inability to mount the file system
From Grub using advanced options I can eventually "resume" through 4.15.0-34-generic
 (but not 4.15.0-36 or 4.15.0-38!) - but it does not (unsurprisingly) resume the previous session

Thanks

---

