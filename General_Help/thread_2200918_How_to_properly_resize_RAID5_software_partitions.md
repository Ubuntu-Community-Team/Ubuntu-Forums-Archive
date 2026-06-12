---
title: "How to properly resize RAID5 software partitions?"
date: 2014-01-21
forum: General Help
---

### Post by melilocacr on 2014-01-21
Hi! I'm a fairly new user. I'm trying to resize my software raid partitions. I tried to use GParted but I'm not sure if it supports software RAIDs. If it does, do I resize the partitions on one drive or do I resize the raid? Is there any documentation out there specific to raid partitions? Any guidance would be great. Thanks!

I have Ubuntu Server 10.04

---

### Post by TheFu on 2014-01-22
Is LVM or encryption involved?
Do you want to make the partitions larger or smaller?

[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)

---

### Post by melilocacr on 2014-01-23
Thanks for your reply! Neither LVM or encryption are involved. I looked at the link you gave me, but I'm still confused as to the procedure to grow one partition and make the other one smaller. Do I shrink one and then grow the other one or how do I go about this without compromising any data?

Thanks!

---

### Post by TheFu on 2014-01-23
If you can't lose any data, make a 100%, know-you-can-recover-it backup before you begin. Anytime work like this is performed, there is a risk of data loss.

As to the answer to your question about order ... think about the steps. If the storage being reduced is needed for the storage to be expanded, then it is clear. Otherwise, it probably doesn't matter.

---

### Post by melilocacr on 2014-01-30
I tried to follow the instruction on the link you provided. When using the rescue console (with the root file system mounted) I get an error message on the first line, when activating the modules. The command is modprobe md. I get an error message that says: FATAL module not found. I'm not sure how to address that issue. Most people online are using it in a different context. Any ideas?

---

### Post by TheFu on 2014-01-31
To get help, please copy/paste the TEXT into a "code" block from the "Adv Reply" form here.  Put the complete command and the relevant output from that command, including any error/warning messages.

If the module is not found, there are 2 issues to look/correct.
* the module cannot be loaded from the expected place - check your "recovery" setup and environment
* the module has not been built for the kernel; it will need to be found and built, and placed in the expected location for the specific sort of module

I would guess that the first is the real issue, lacking any other data.

Did you export the mdadm.conf file successfully, per the instructions?

---

### Post by melilocacr on 2014-03-25
Thanks for your reply. I still can't load the modules and I've been looking into other options to complete my task. The recovery environment being used is the one that comes with the Ubuntu Server cd. The module does exist for the kernel and I see it on the list of modules. 

The file mdadm.conf was exported successfully, without the loaded modules though. 

Do you think this website attempts to do the same thing I wanna do?

[http://doc.opensuse.org/products/draft/SLES/SLES-storage_sd_draft/raidresize.html](http://doc.opensuse.org/products/draft/SLES/SLES-storage_sd_draft/raidresize.html)

Let me know what else I can do.

Thank you

---

### Post by TheFu on 2014-03-25
Already answered:
> To get help, please copy/paste the TEXT into a "code" block from the "Adv Reply" form here. Put the complete command and the relevant output from that command, including any error/warning messages.


---

### Post by melilocacr on 2014-03-26
Attempted to follow the instructions and now I can't access my system. When booting I get the following error messages:

```
fsck from util-linux-ng 2.17.2
/dev/md0: clean, 71111/1222992 files, 365305/4882432 blocks
The disk drive for /home is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery
```

I can skip mounting and access the root partition but I can't mount the one I tried to resize. 

Here are the commands I used to shrink it

```

#modprobe md
FATAL: Module not found
#modprobe linear
FATAL: Error inserting linear (/lib/modules/2.6.32-38-generic/kernel.drivers/md/linear.ko): Invalid module format
#modprobe multipath
FATAL: Error inserting multipath (/lib/modules/2.6.32-38-generic/kernel.drivers/md/multipath.ko): Invalid module format
#modprobe raid0
#modprobe raid1
#modprobe raid5
#modprobe raid6
#cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf_orig
#mdadm --examine --scan >> /etc/mdadm/mdadm.conf
#mdadm -A --scan
#e2fsck -f /dev/md1
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Cheking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/md1: 56/1966080 files (0.0% non-contiguous), 167447/7864320 blocks
#resize2fs /dev/md1 25G
resize2fs 1.41.11 (14-Mar-2010)
Resizing the filesystem on /dev/md1 to 6553600 (4k) blocks.
The filesystem on /dev/md1 is now 6553600 blocks long. 
#mdadm --grow /dev/md1 --size=31457280
#resize2fs /dev/md1
resize2fs 1.41.11 (14 Mar-2010)
Resizing the filesystem on /dev/md1 to 7864320 (4k) blocks.
The filesystem on /dev/md1 is now 7864320 blocks long. 

```

Any ideas?

---

### Post by melilocacr on 2014-03-27
I forgot to mention that the partition I want its size to increase is not contiguous to the one that I'm decreasing. How do I set it up so the partition uses the free space? Do I need to move the partitions? Thank you

---

