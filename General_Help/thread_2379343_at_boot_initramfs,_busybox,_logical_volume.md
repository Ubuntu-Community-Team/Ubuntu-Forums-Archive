---
title: "at boot initramfs, busybox, logical volume"
date: 2017-12-04
forum: General Help
---

### Post by verenard on 2017-12-04
Hiya,

I have an ubuntu install that doesn't boot into OS but I get the initramfs prompt instead.

It's an installation with a logical volume so I've tried also to mount the logical volume in Ubuntu and with windows tools. I can see the partitions but can't get into my files.

I either want to make my HDD bootable again or get the data off it by mounting it.

I've tried various things from forums, like fsck, but for that I get an error fsck: not found.
I get a report like this when I boot[INDENT]
[  37.272796] EXT4-fs (dm-0): unable to read superblock
[  37.272966] sd1:0:0:0: [sdb]
[  37.273027] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  37.273090] sd:1:0:0:0: [sdb] CDB:
[  37.273149] Read(10): 28 00 00 07 b0 00 00 00 01 00
[  37.273721] end request: I/O error, dev sdb, sector 503808
[  37.273788] FAT-fs (dm-0): unable to read boot sector
Mount: mounting /dev/dm-0 on /root failed: Invalid argument
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: no such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed:No such file or directory
target filesystem doesn't have requested /sbin/init.
No init found. try passing init= bootarg.
BusyBox v1.21.....blah...Enter 'help'...blah
(initramfs)
[/INDENT]

does bad sectors mean my HDD is damaged ?

Also, if I enter 'Exit' at the initramfs prompt, I get a load of kernel panic and other stuff.
What to do :confused:

---

### Post by Kirk Schnable on 2017-12-04
> **verenard said:**
> does bad sectors mean my HDD is damaged ?
Quite likely, yeah.  These are not a good sign:

> **verenard said:**
> [  37.272796] EXT4-fs (dm-0): unable to read superblock
> **verenard said:**
> [  37.273721] end request: I/O error, dev sdb, sector 503808

> **verenard said:**
> What to do :confused:
I would suggest boot to a Live CD first, from there you should have access to more tools.  The initramfs console is a very basic shell and it won't have a lot of commands that are helpful for troubleshooting these types of issues.

I would try running a smart test on the drive (**smartctl -t short /dev/sdb** where /dev/sdb is the disk to test), then take a look at the smart stats on the drive (**smartctl -a /dev/sdb** where /dev/sdb is the disk in question).

You may be able to try an FSCK on the volume from the live environment, but I would check the drive health first and decide if that's a wise idea.  If you're not sure how to interpret the smart stats, you can post them here for us to review.

---

### Post by verenard on 2017-12-05
Thanks for your reply. The drive in question is one of several in my PC, I can unmount it and run fsck from my usual OS ? BTW I looked at other forum answers for this that say use fsck, so I was surprised I get an error saying it doesn't exist in initramfs shell. Have they changed it ?
I'll run smartctl on it.

---

### Post by verenard on 2017-12-05
Thanks for your reply. 

I try mounting it to run smart tests but get.

Error mounting  /dev/sdb1 at /media/rtz/0f73f40d-4de7-4251-9632-685ac8ee5716:  Command-line `mount -t "ext2" -o "uhelper=udisks2,nodev,nosuid"  "/dev/sdb1" "/media/rtz/0f73f40d-4de7-4251-9632-685ac8ee5716"' exited  with non-zero exit status 32: mount: wrong fs type, bad option, bad  superblock on /dev/sdb1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
 (udisks-error-quark, 0)

I know it will sometimes mount and I can see the kernel and boot files in the first 255MB, but sometimes it doesn't mount so I think it has dodgy hardware. I unplug and plug it in again.

Can I fsck on it ?

---

### Post by verenard on 2017-12-05
If I have disk A with my OS on it, and disk B with an LVM volume, can I extend the logical volume on disk B onto disk A and shift data from B to A ?

---

### Post by verenard on 2017-12-09
Seems it's a bad hard drive with input output errors. 
I want to copy as much of it as I can on to a back up disk. Would ddrescue be good ? What sort of formatting should I do on the spare disk ?

---

### Post by verenard on 2017-12-09
Seems it's a bad hard drive with input output errors. 
I want to copy as much of it as I can on to a back up disk. Would ddrescue be good ? What sort of formatting should I do on the destination disk ?

---

