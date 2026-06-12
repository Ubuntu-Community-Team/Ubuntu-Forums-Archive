---
title: "Unable to mount 16 GB Filesystem"
date: 2013-01-21
forum: General Help
---

### Post by SuperFreak on 2013-01-21
I removed a USB key that had a baremetal backup of my system too quickly (thought i had unmounted it but it hadn't finished writing to the key) and now I can't mount it. I get the following error:

```
Unable to mount 16 GB Filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

I ran lsusb and  dmesg | tail got the following:

```
desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 003: ID 04f9:01f5 Brother Industries, Ltd 
Bus 002 Device 004: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 005: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse

```
I don't see the Adata USB key there

and:

```
$ dmesg | tail  or so
tail: cannot open `or' for reading: No such file or directory
tail: cannot open `so' for reading: No such file or directory
david@david-desktop:~$ dmesg | tail
[ 2494.184428] EXT4-fs error (device sdd1): ext4_put_super:818: Couldn't clean up the journal
[ 2494.184436] EXT4-fs (sdd1): Remounting filesystem read-only
[ 2494.184438] EXT4-fs (sdd1): previous I/O error to superblock detected
[ 2494.184722] EXT4-fs (sdd1): unable to read superblock
[ 2494.185250] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880414cc3540
[ 2494.185255] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880414cc3500
[ 2514.142677] xhci_hcd 0000:00:14.0: Timeout while waiting for a slot
[ 2514.142684] hub 4-0:1.0: couldn't allocate port 3 usb_device
[ 2614.600725] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:d8:5d:4c:f3:84:db:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 2739.361772] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:d8:5d:4c:f3:84:db:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
```

Is it possible to fix this without losing my backup?

---

### Post by sudodus on 2013-01-21
You can't mount it, but can you see the drive with
```
sudo fdisk -lu
```
and can you see any partition?

Please post the output of that command!

If you can see the partition, you can repair the file system. *Edit*: I think this will be possible.

If not there are repair tools for the partition, but before spending too much time on it answer this question:

Are the original data still available (is your system and your personal data good)?

If this is the case it is probably easier to wipe the damaged USB pendrive, reformat it and make a new backup.

---

### Post by greg_ory on 2013-01-21
I am wondering if it would make a difference when you stick it into a different system if available. I guess that would be to easy but was working for me in the past :-)

---

### Post by SuperFreak on 2013-01-21
I was using USB 3 connection which up to my hasty removal worked fine but doesn't now. However USB 2 connections seem to mount and recognize the USB Key. Here is the output of $ sudo fdisk -lu I don't see the USB key.


```
$ $ sudo fdisk -lu
[sudo] password for david: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

[sudo] password for david: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

```

Perhaps the best solution is for me to put it in a USB 2 connection reformat the USB key and rerun Redo to replace the baremetal backup of my system. What do you think?

---

### Post by sudodus on 2013-01-21
You can always try to repair it via the USB2 port, if the computer can see the partition that way. What file system is it?

Repair Windows file systems with Windows
```
chkdsk /f X:
```
and linux ext file systems with
```
sudo e2fsck -f /dev/sdxy
```
where X and x should be substituted with the proper driver letter and y with the partition number.

If this doesn't work, go ahead and make a new backup!

But I suggest that you consider a safer medium for backup. A USB HDD is safer than a USB pendrive.

I think you will remember to let it finish writing in the future, and you can use the terminal window command ```
sync
``` to check that it finishes writing. It should not return to prompt until the writing has finished.

---

### Post by SuperFreak on 2013-01-21
Funny thing. I decided to try rebooting the computer and the USB key was then recognized in the USB port. I will mark this as, hopefully, solved

---

