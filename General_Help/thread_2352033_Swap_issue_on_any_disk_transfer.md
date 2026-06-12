---
title: "Swap issue on any disk transfer"
date: 2017-02-08
forum: General Help
---

### Post by Graham_Bartlett on 2017-02-08
Hi    I have a ubuntu issue when transferring files from one drive to another.  Usually usb drives but happens on internal drive also.  kswapd0  runs quickly to 100% or close to it and system gradually slows. With large files i have been implementing the following.....echo 3 > /proc/sys/vm/drop_caches  on a root terminal.  This appears to keep the transfer going, not perfect but transfer will complete.  If i dont run this command system will grind to a stop and is not controllable if transfer isnt able to be terminated.  I have a fairly new desktop with ssd drive and a few external drives of various types. Plenty of space left on them.  This hasnt always been the case as files transferred quite well some time back.  I have tried booting with kernels back to 30 and issue still occurs, so perhaps its been some time that they have been working well.  Kernels previous dont work correctly i think de to a new graphics card that i installed but not certain on that !   I havnt run backups just recently. This issue occurred while backing up my home directory do an external device.  Mostly usb3 devices but not expecting top performance because not all usb slots are 3   , but when the transfer grinds down to 2mbs i think we have a kernel issue.  Has anybody seen this or know of a bug fix ?
Thanks
Graham

---

### Post by kingneutron on 2017-02-10
> With large files i have been implementing the following.....echo 3 >  /proc/sys/vm/drop_caches  on a root terminal.  This appears to keep the  transfer going, not perfect but transfer will complete.  If i dont run  this command system will grind to a stop and is not controllable if  transfer isnt able to be terminated.

--DON'T DO THAT if you have outstanding I/O going on, you may not be able to guarantee data integrity (files that end up on the destination drive may be corrupted.)  Always do a 'sync' before doing that command to be safe if you're trying to free up memory.

--That command frees pagecache, dentries AND inodes.  I have recently had issues copying data to an extremely slow usb2 drive, it slowed down the whole 6-core system, and that is with 64-bit kernel 4.8.10.  I finally killed the copy, transferred the files over network and moved them to the usb2 drive on another system that wasn't being used interactively.

--There can be several issues causing this:

o Kernel elevator (CFQ,deadline) 

o /etc/fstab options - How the drive(s) are mounted (noatime,data=writeback,filesystem being used)

o Drive may be failing or may be a cabling issue -- may need to do a SMART drive test or fsck

---

--Posting more info on your system and drives may help with resolving this. 

--How much RAM do you have?  Post results of $ **free**

--Also post results of the following:

$ **dmesg | grep 'Command line'**    # we are looking for i/o scheduler

( this is how mine looks )
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.8.10-antix.1-amd64-smp root=UUID=264d2bdc-d4df-4d76-a1dc-3096a5e68bb1 ro zswap.zpool=zsmalloc vga=788 quiet

$ **cat /sys/block/sda/queue/scheduler**   # what I/O scheduler/elevator is being used on a particular drive

( this is how mine looks for the 1st hard drive )
$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 

REF: [https://access.redhat.com/solutions/5427](https://access.redhat.com/solutions/5427)


(as root) # **apt-get update;apt-get install  smartmontools**    # only need to do this ONCE

(as root) # **for d in /dev/sd?;do smartctl -a $d |head -n 16;done**     # this will give information about your connected drives

$ **mount**     # this will show mount options for all connected drives/partitions (noatime, data=ordered, et cetera )

---

### Post by HermanAB on 2017-02-10
For large file transfers, I drop to the terminal and use ionice and cp since there seems to be a recurrent bug in the USB subsystem.  The same bug resurfaces every few years.

---

