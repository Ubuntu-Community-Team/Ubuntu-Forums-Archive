---
title: "How to recover lost ext3 partition?"
date: 2007-01-28
forum: General Help
---

### Post by runeberge on 2007-01-28
Hi.

I have a 500GB MyBook USB hard drive which has two partitions. One small 10 GB NTFS partition, and a large ext3 partition which uses up the rest. 

Recently the ext3-partition has just disappeared. It does not get mounted when the disk is connected, and gparted lists it as "unknown" in the file system column. 

Here's output from fdisk:

```

# fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1338    10747453+   7  HPFS/NTFS
/dev/sda2            1339       60801   477636547+  83  Linux

```Any tips to what I can do to recover my data?

---

### Post by chalex on 2007-01-28
Have you tried running the manufacturer's diagnostic utility?

---

### Post by taurus on 2007-01-28
What happens when you run these commands from a terminal?

```
sudo mkdir /media/sda2
sudo mount -t ext3 /dev/sda2 /media/sda2
df -h
```

---

### Post by runeberge on 2007-01-28
chalex: No, I haven't. I will look into that. 

taurus:
```

# mount -t ext3 /dev/sda2 /media/sda2
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

# dmesg | tail 
[17179615.432000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179615.596000] NFSD: starting 90-second grace period
[17179624.920000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179624.936000] NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17179625.300000] NTFS volume version 3.1.
[17187567.108000] usb 4-3: reset high speed USB device using ehci_hcd and address 2
[17187682.896000] usb 4-3: reset high speed USB device using ehci_hcd and address 2
[17191713.304000] usb 4-3: reset high speed USB device using ehci_hcd and address 2
[17191715.116000] VFS: Can't find ext3 filesystem on dev sda2.
[17191831.276000] VFS: Can't find ext3 filesystem on dev sda2.


```

---

### Post by taurus on 2007-01-28
Do you have any important files on /dev/sda2?  You can install fs-driver for your XP and see if you can access /dev/sda2 from your Windows.

[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by runeberge on 2007-01-28
I have some files which I'd really like to recover there. When I try to access it in Windows using fs-driver I get a message saying "The disk in drive X is not formatted. Do you want to format it now?". The IFS control panel does identify it as "Linux"

---

### Post by highneko on 2007-01-28
I always thought ext3 permanently deletes files when you delete them. Good luck.

---

### Post by runeberge on 2007-01-28
> **highneko said:**
> I always thought ext3 permanently deletes files when you delete them. Good luck.

I haven't deleted any files. The partition just stopped working.

---

### Post by highneko on 2007-01-28
> **runeberge said:**
> I haven't deleted any files. The partition just stopped working.

Ok. I should have read your post instead of just the thread title. Have you done anything recently you suspect may have caused this?

---

### Post by runeberge on 2007-01-28
No, not that I can think of

---

### Post by taurus on 2007-01-28
Maybe you want to run fsck /dev/sda2.

```
sudo fsck -C /dev/sda2
```

---

### Post by runeberge on 2007-01-29
I tried to run fsck and here is the result:

```

# fsck -C /dev/sda2
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
Couldn't find ext2 superblock, trying backup blocks...
/dev/sda2 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 9109706 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error<y>? yes

Force rewrite<y>? 

# dmesg | tail
[17190619.192000] Buffer I/O error on device sda2, logical block 14
[17190619.192000] lost page write due to I/O error on sda2
[17190619.192000] Buffer I/O error on device sda2, logical block 15
[17190619.192000] lost page write due to I/O error on sda2
[17190619.192000] Buffer I/O error on device sda2, logical block 16
[17190619.192000] lost page write due to I/O error on sda2
[17190619.192000] Buffer I/O error on device sda2, logical block 17
[17190619.192000] lost page write due to I/O error on sda2
[17190619.192000]  0:0:0:0: rejecting I/O to dead device
[17190619.196000]  0:0:0:0: rejecting I/O to dead device

```

As I wasn't sure what "Force rewrite" does I terminated it. It seems there is a hardware error on the drive, so I will run the Western Digital diagnostics utility on it, but it estimated it to take 6 hours, so I'll put it on tomorrow while I'm at work.

I tried googling a bit for these error messages, but what I found got very technical...

---

### Post by runeberge on 2007-02-04
Looks like my USB controller is the problem. I connected it to another computer, and was then able to repair it with fsck. Thanks for the help guys!

---

