---
title: "disk problems"
date: 2014-04-01
forum: General Help
---

### Post by NyteRukh on 2014-04-01
hi i am running ubuntu 64 bit on a lenova g530. everything was running fine booting and starting. then two days ago i started getting errors during the boot process something with the sda and sda5 and a logical block, i cant find the boot log that has it. and when i run selfcheck on the disk i get two errors 

4 start...unt 125804 1 20 1 oldage online failing

189 high...rites 2588 1 45 1 oldage online failing

is there a disk repair utility i can use to fix it..or how would i fix it?:(
heres what the log says

kernel: [  217.899375] end_request: I/O error, dev sda, sector 482189321
kernel: [  217.899378] Buffer I/O error on device sda5, logical block 1
kernel: [  217.899388] ata1: EH complete
kernel: [  220.378390] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
kernel: [  220.378394] ata1.00: irq_stat 0x40000008
kernel: [  220.378398] ata1.00: failed command: READ FPDMA QUEUED
kernel: [  220.378403] ata1.00: cmd 60/08:08:08:a0:bd/00:00:1c:00:00/40 tag 1 ncq 4096 in
kernel: [  220.378403]          res 41/40:08:09:a0:bd/00:00:1c:00:00/40 Emask 0x409 (media error) <F>
kernel: [  220.378406] ata1.00: status: { DRDY ERR }
kernel: [  220.378408] ata1.00: error: { UNC }
kernel: [  220.382773] ata1.00: configured for UDMA/100

---

### Post by sudodus on 2014-04-01
You can try to fix it wih e2fsck, when booted from another drive, for example the Ubuntu install C/DVD/USB drive.

```
sudo e2fsck -cf /dev/sdxy
```

where x is the driver letter, a in your case, and y is the partition number. You may need to do it for all the ext4 partitions (you have a root partition, and maybe some other partitions too). But don't use it for the swap partition. So it might be **/dev/sda1** and/or **/dev/sda2 ** or **/dev/sda5**. Often /dev/sda5 is swap, which should *not* be treated with e2fsck.

See ```
man e2fsck
``` for a detailed description.

This command may take an hour (can be much more or less) depending on the size of the partition an how severe problems there are.

---

### Post by NyteRukh on 2014-04-01
so my code would be [COLOR=#000000][FONT=Ubuntu Mono]sudo e2fsck -cf /dev/sda1 ??[/FONT][/COLOR]

---

### Post by NyteRukh on 2014-04-01
ty ill give it a try

---

### Post by sudodus on 2014-04-01
You can check with

```
sudo parted -l
```
and
```
sudo fdisk -lu
```

which ext4 partititions there are. Post the output in a reply if you want help to interpret what it means. Otherwise, yes,

```
sudo e2fsck -cf /dev/sda1 
```

is correct if your ext4 partition (the root partition) is the first partition on the first drive: /dev/sda1

---

### Post by NyteRukh on 2014-04-02
ok i ran e2fsck on /dev/sda1 and it still did it...i did parted -l on the hd besides sda1 i have sda2 which is extended and sda5 which is logical im going to try running e-e2fsck on /dev/sda2 and see if it works..but from i get looking at the log is that the problem lies in the logical(sda5) if it is how would i repair it..and thanks for all your help

---

### Post by sudodus on 2014-04-02
No, don't run it on the extended partition. And check what kind of partition is sda5. Run e2fsck only on linux ext partiitons, not on a swap partition.

---

### Post by NyteRukh on 2014-04-02
its an extended or logical partition

---

### Post by sudodus on 2014-04-03
The extended partition is only a container for logical partitions.

Logical partitions can be formatted to ext4 or fat32 or be swap partitions (just like primary partitions), so check the partition /dev/sda5. Only if it is an ext partition (ext2, ext3 or ext4) you should use the e2fsck command.

---

### Post by efflandt on 2014-04-03
Note that hard drives reserve some space to automatically transparently remap good sectors in place of bad sectors regardless of OS. So if you actually start seeing bad sectors or errors like this, even if you can temporarily fix it with e2fsck, it sounds like the drive is failing and you should back up or copy anything from the drive that you want to keep that is not already backed up. I don't know exactly what DRDY ERR means, but it sounds like "dirty" and when I see that along with end_request errors I know that a drive is failing.

Note that if that happens to a partition Linux is running from, one sign may be that that you no longer have write permission because it has remounted the partition read-only, which can also prevent logs about the errors from being saved, which you may be able to see by running dmesg before shutting it down. That happened to me last year with a 3 year old drive on my desktop last year and I nursed it along for awhile by locking out badblocks with e2fsck, until it got to the point that it would remount read-only about every time I let it run for awhile. But I knew it could fail at any time and had another Ubuntu system with grub on separate SSD. So I eventually replaced the failing drive.

But I don't know if or how it can be fixed if the problem is in a swap partition, other than commenting out (begin line with #) for anything in /etc/fstab regarding swap. I don't even have any swap on my desktop because it has 8 GB RAM and I do not hibernate.

---

### Post by NyteRukh on 2014-04-03
ok i commented out the line in fstab that had to do with swap...and it still came up with the errors...so the hd could be on its way out. other than the errors during boot, the system runs fine. so im going to nurse this along untill i can buy a new laptop

---

### Post by sudodus on 2014-04-03
You can use ***ddrescue*** to clone it to another drive to save as much as possible of the data. Do not use a failing drive. Wait until you can run the rescue operation.

See this link with some details about ddrescue.

[http://ubuntuforums.org/showthread.php?t=2214816&p=12976037#post12976037](http://ubuntuforums.org/showthread.php?t=2214816&p=12976037#post12976037)

---

