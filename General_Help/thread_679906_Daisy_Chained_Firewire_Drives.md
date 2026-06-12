---
title: "Daisy Chained Firewire Drives"
date: 2008-01-27
forum: General Help
---

### Post by RC-Aloc on 2008-01-27
Hello Ubuntu Forums.

Description:
I've been running Gutsy 7.10 for several months now on a MacMini (C2D,1.83MHz,2GB RAM) with an attached Firewire (IEEE1394) Drive, an Acomdata MiniPal, (/dev/sdb1) housing a file server.  I needed to expand storage space, purchased another mini pal, plugged it in (daisy chained to the other drive because the MacMini only has one Firewire port), partitioned and formated with ext3, added the appropriate line in fstab, rebooted, the rEFIt bootloader starts and then I get a black screen.  No cursor, no GRUB menu, nothing.  :confused:

Troubleshooting:
1. Unplugged the new (daisy chained) drive and the computer boots up normal
2. Unplugged the old drive and connected it directly to the MacMini and boots up fine
3. Left the drives daisy chained, left the first hard drive off, turned on the new hard drive and the computer boots up normal
4. I can't get a dmesg output when they're both plugged in, because my computer won't boot

Outputs:
1. /etc/fstab lines:
```
/dev/sdb1	/media/Backup	ext3	defaults		0	0
/dev/sdc1	/media/Music	ext3	defaults		0	0
```
2. /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
```
3. /etc/initramfs-tools/initramfs.conf
```
#
# initramfs.conf
# Configuration file for mkinitramfs(8). See initramfs.conf(5).
#

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=most

# BUSYBOX: [ y | n ]
#
# Use busybox if available.
#

BUSYBOX=y

#
# NFS Section of the config.
#

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# DEVICE: ...
#
# Specify the network interface, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

```
4. /etc/initramfs-tools/modules
```
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
```

Postulations:
1. should I have ieee1394 and ohci1394 load on startup?
2. does the system think I'm trying to perform RAID with these identical hard drives?

Any help would be greatly appreciated.

---

