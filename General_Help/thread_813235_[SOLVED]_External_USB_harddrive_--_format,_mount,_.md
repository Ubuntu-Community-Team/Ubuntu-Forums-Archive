---
title: "[SOLVED] External USB harddrive -- format, mount, use"
date: 2008-05-30
forum: General Help
---

### Post by slafochmed on 2008-05-30
Hi there,

I am using Ubuntu Server 6.10 on a Mac Mini PowerPC.
Right now I am trying to make a big external usb harddrive accessible. I am a Linux noob so there could be strange questions / actions. ;)

I connected via USB and did this:

```
tail /var/log/messages
```

->  Attached scsi generic sg0 type 0

now I tried fdisk

```
fdisk /dev/sg0
```

and get into a command mode
but I do not know what to do next.

'n' does not work

'p' results into
No partition map exists

'?' results into
Commands are:
  h    help
  p    print the partition table
  P    (print ordered by base address)
  i    initialize partition map
  s    change size of partition map
  b    create new 800K bootstrap partition
  c    create new Linux partition
  C    (create with type also specified)
  d    delete a partition
  r    reorder partition entry in map
  w    write the partition table
  q    quit editing (don't save changes)

I would like to simply have one big partition. I want to use the external harddisk for backup occassionally. It would be great if I could access it in windows, too.

The harddrive is 750 GB with own power supply.

Now I did the following:
> Command (? for help): i
size of 'device' is 0 blocks:
new size of 'device' is 4 blocks
Command (? for help): p
/dev/sg0
        #                    type name                length   base    ( size )  system
/dev/sg01     Apple_partition_map Apple                    2 @ 1       (  1.0k)  Partition map
/dev/sg02              Apple_Free Extra                    1 @ 3       (  0.5k)  Free space

Block size=512, Number of Blocks=4
DeviceType=0x0, DeviceId=0x0


---

### Post by slafochmed on 2008-06-01
:) I have it working now.

I chose the following solution:
- Format it NFTS
- Make my linuxbox (macmini) read and write to NFTS

Format it NFTS:
Simple, I just formatted it in Windows.

Linux read/write to NFTS:
I installed [FUSE]("http://linux.softpedia.com/get/System/Filesystems/Filesystem-in-Userspace-1456.shtml").
Then I installed
[ntfs-3g]("http://linux.softpedia.com/get/System/Hardware/ntfs-3g-15028.shtml")

Then I connected my external USB harddrive.
To check what is its device name I did:
```
tail /var/log/messages
May 31 23:03:37 macmini kernel: [13025831.927303] scsi2 : SCSI emulation for USB Mass Storage devices
May 31 23:03:42 macmini kernel: [13025836.926682]   Vendor: ST375064  Model: 0A                Rev: 0811
May 31 23:03:42 macmini kernel: [13025836.926700]   Type:   Direct-Access                      ANSI SCSI revision: 00
May 31 23:03:42 macmini kernel: [13025836.929359] SCSI device sda: 1465149168 512-byte hdwr sectors (750156 MB)
May 31 23:03:42 macmini kernel: [13025836.930632] sda: test WP failed, assume Write Enabled
May 31 23:03:42 macmini kernel: [13025836.931996] SCSI device sda: 1465149168 512-byte hdwr sectors (750156 MB)
May 31 23:03:42 macmini kernel: [13025836.933241] sda: test WP failed, assume Write Enabled
May 31 23:03:42 macmini kernel: [13025836.933412]  sda: sda1
May 31 23:03:42 macmini kernel: [13025836.951821] sd 2:0:0:0: Attached scsi disk sda
May 31 23:03:42 macmini kernel: [13025836.951881] sd 2:0:0:0: Attached scsi generic sg0 type 0
```

I saw that it is **sda1**.
I mounted it with the freshly installed ntfs-3g:
```
# ntfs-3g /dev/sda1 /media/test
WARNING: Deficient Linux kernel detected. Some driver features are
         not available (swap file on NTFS, boot from NTFS by LILO), and
         unmount is not safe unless it's made sure the ntfs-3g process
         naturally terminates after calling 'umount'. If you wish this
         message to disappear then you should upgrade to at least kernel
         version 2.6.20, or request help from your distribution to fix
         the kernel problem. The below web page has more information:
         http://ntfs-3g.org/support.html#fuse26
```

I then could read/write to it easily. :)

To disconnect I simply issued umount:
```
umount test
```
To be sure that it is unmounted I checked if the ntfs-3g process was really killed:
```
ps -A
```
...it was not there, so good.
if it was I would have killed it by
```
kill <process nr of nfts-3g>
```

Great. :)

By the way, the command for zipping folders is:
```
zip -9 -r <zip file> <folder name>
```

---

