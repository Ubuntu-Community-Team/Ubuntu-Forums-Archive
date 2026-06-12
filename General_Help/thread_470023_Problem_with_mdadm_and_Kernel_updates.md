---
title: "Problem with mdadm and Kernel updates"
date: 2007-06-10
forum: General Help
---

### Post by BgPup on 2007-06-10
First my problem, then the configuration:

Problem
Attempts to update kernel and initramfs produces the following errors:

```

user@ubuntu:~$ sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
update-initramfs: lilo run failed for /boot/initrd.img-2.6.20-16-generic:

Fatal: raid_setup: stat("/dev/hda")
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
update-initramfs: lilo run failed for /boot/initrd.img-2.6.20-15-generic:

Fatal: raid_setup: stat("/dev/hda")
update-initramfs: Generating /boot/initrd.img-2.6.17-11-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
update-initramfs: lilo run failed for /boot/initrd.img-2.6.17-11-generic:

Fatal: raid_setup: stat("/dev/hda")
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
update-initramfs: lilo run failed for /boot/initrd.img-2.6.17-10-generic:

Fatal: raid_setup: stat("/dev/hda")

```

Can I get rid of mdadm?  I don't recall this package having been present when I was using Edgy.

Configuration:
I'm running Feisty on an old Dell 686 box with two IDE drives.  I have them configured as follows

on hda I have two partitions, one vfat (win98se) and one Ext3 that I use to dump stuff when I need to put something on another disk.

hdb is my ubuntu disk and it has one partition that is the only physical volume for ubuntu lvg which has separate logical volumes for / and /home and swap.  No RAID arrays at all.

I've seen alot of stuff about how to fix this kind of thing when RAID arrays are involved, but nothing when it's just LVM and a plain vanilla physical volume.  I've tried uninstalling mdadm, but chickened out after the warnings it threw up.

Almost forgot:
mdadm.conf reads:

```

DEVICE partitions
MAILADDR root

```

---

### Post by pt123 on 2007-06-10
when upgrading over to Fiesty change your device names in /boot/grub/menu.lst  to use UUID than hdaX becuase all disk drives are refered by sdaX in Fiesty and this I think confuses mdadm.

Also changing the main drives in /etc/fstab might help too.

---

### Post by briguy on 2007-06-20
I have the same problem, however I'm not sure how to change the labels to the UUID - how should my fstab look after I change it?

---

