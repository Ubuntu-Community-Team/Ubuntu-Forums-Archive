---
title: "Unable to boot 14.04.01 - motherboard raid"
date: 2014-10-27
forum: General Help
---

### Post by sgoranov on 2014-10-27
Hi,
I'm installed successful Ubuntu 14.04.01 but after that I'm not able to boot it. I've got following hdd configuration:

motherboard raid 0 (2 hdd's)
motherboard raid 1 (2 hdd's)
sdd in jbod
hdd in jbod - two partitions, was recognized as /dev/sdf with /dev/sdf1 and /dev/sdf2. Ubuntu was installed on /dev/sdf2 and the  Grub was installed on /dev/sdf

When I choose to boot from last hdd (where the grub was installed) I see grub rescue prompt with following message:
"disk hdd0 not found"

After following commands:
> set debug=all
ls -l

The output is:
> opening hd0
opening hd0 failed
closing hd0
error disk hd0 not found


Any help is appreciated, thanks in advance!

---

### Post by sgoranov on 2014-11-01
The problem still exists. I tried to install Ubuntu on USB flash drive and the error is the same while trying to boot from that flash drive - grub is not able to find any drive at all and the error is "disk hd0 not found". The ls command shows nothing.
I installed mdraid09 and mdraid1x mods but the result is till the same. Modified grub.cfg manually to start those modules right after insmod ext2 - the same result.
Any ideas how to solve the issue?

---

