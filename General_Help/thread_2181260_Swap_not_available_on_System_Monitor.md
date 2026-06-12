---
title: "Swap not available on System Monitor"
date: 2013-10-17
forum: General Help
---

### Post by z_space on 2013-10-17
I had a swap partition of 1GB (RAM 1GB, Ubuntu 12.04 lts). Now swap is  not shown on System Monitor neither can I hibernate my pc (sudo  pm-hibernate).

**blkid output:**

  /dev/sda1: UUID="B8B4FBB1B4FB706C" TYPE="ntfs" 
/dev/sda2: UUID="2ea7d608-2d89-4e41-9436-d05cb3ce8871" TYPE="swap" 
/dev/sda3: UUID="3219d03a-67e4-454b-8ce7-a27831846e35" TYPE="ext4" 
/dev/sda5: LABEL="Softwares" UUID="AC1CC3301CC2F47C" TYPE="ntfs" 
/dev/sda6: LABEL="Education" UUID="1E103E6C103E4B53" TYPE="ntfs" 
/dev/sda7: LABEL="Recreation" UUID="2CC8D181C8D149AA" TYPE="ntfs" 
/dev/sda8: LABEL="Miscellaneous" UUID="0274D6B174D6A727" TYPE="ntfs" 



[B]/etc/fstab
[/B]
  # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda6 during installation 
UUID=3219d03a-67e4-454b-8ce7-a27831846e35 /               ext4    errors=remount-ro 0       1 
# swap was on /dev/sda5 during installation 
UUID=2ea7d608-2d89-4e41-9436-d05cb3ce8871 none            swap    sw              0       0 [B]


free -m[/B]

total       used       free     shared    buffers     cached
Mem:           991        869        121          0         44        354
-/+ buffers/cache:        470        520
Swap:            0          0          0


**cat /proc/swaps**

  Filename                Type        Size    Used    Priority


**fdisk -l**

  Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f369f36

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31471334    15735636    7  HPFS/NTFS/exFAT
/dev/sda2        31471616    33470447      999416   82  Linux swap / Solaris
/dev/sda3        33472512    62539775    14533632   83  Linux
/dev/sda4        62541045   312592769   125025862+   f  W95 Ext'd (LBA)
/dev/sda5        62541108   125066024    31262458+   7  HPFS/NTFS/exFAT
/dev/sda6       125066088   187591004    31262458+   7  HPFS/NTFS/exFAT
/dev/sda7       187591068   250115984    31262458+   7  HPFS/NTFS/exFAT
/dev/sda8       250116048   312576704    31230328+   7  HPFS/NTFS/exFAT


Finally,** swapon --all**

  swapon: /dev/sda2: swapon failed: Invalid argument


Please help. Thanks in advance.

---

### Post by z_space on 2013-10-17
bump!!

---

### Post by plucky on 2013-10-17
> blkid output:

/dev/sda1: UUID="B8B4FBB1B4FB706C" TYPE="ntfs"
/dev/sda2: UUID="2ea7d608-2d89-4e41-9436-d05cb3ce8871" TYPE="swap"
/dev/sda3: UUID="3219d03a-67e4-454b-8ce7-a27831846e35" TYPE="ext4"
/dev/sda5: LABEL="Softwares" UUID="AC1CC3301CC2F47C" TYPE="ntfs"
/dev/sda6: LABEL="Education" UUID="1E103E6C103E4B53" TYPE="ntfs"
/dev/sda7: LABEL="Recreation" UUID="2CC8D181C8D149AA" TYPE="ntfs" 

Is that the same when you use ```
sudo blkid
```?

Try ```
ls -l /dev/disk/by-uuid
``` to see if the uuid is the same.

Good Luck

---

### Post by z_space on 2013-10-17
> **plucky said:**
> Is that the same when you use ```
sudo blkid
```?

Yes.

> Try ```
ls -l /dev/disk/by-uuid
``` to see if the uuid is the same.

Yes the UUID is the same (as also reflected in fstab).

```
ls -l /dev/disk/by-uuid
```
total 0
lrwxrwxrwx 1 root root 10 Oct 18 00:00 0274D6B174D6A727 -> ../../sda8
lrwxrwxrwx 1 root root 10 Oct 18 00:00 1E103E6C103E4B53 -> ../../sda6
lrwxrwxrwx 1 root root 10 Oct 18 00:00 2CC8D181C8D149AA -> ../../sda7
lrwxrwxrwx 1 root root 10 Oct 18 00:00 2ea7d608-2d89-4e41-9436-d05cb3ce8871 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 18 00:00 3219d03a-67e4-454b-8ce7-a27831846e35 -> ../../sda3
lrwxrwxrwx 1 root root 10 Oct 18 00:00 AC1CC3301CC2F47C -> ../../sda5
lrwxrwxrwx 1 root root 10 Oct 18 00:00 B8B4FBB1B4FB706C -> ../../sda1

---

### Post by plucky on 2013-10-18
Do you have gparted installed?

If yes, launch gparted and see what that makes of the swap partition.(post screenshot)

If it is ok,you could try deleting and recreating the swap partition again and see if anything changes.

How did you create the swap partition?

The installer normally tries to put it into the extended partition.

---

### Post by z_space on 2013-10-18
> **plucky said:**
> Do you have gparted installed?

If yes, launch gparted and see what that makes of the swap partition.(post screenshot)

If it is ok,you could try deleting and recreating the swap partition again and see if anything changes.

How did you create the swap partition?

The installer normally tries to put it into the extended partition.
[ATTACH=CONFIG]247031[/ATTACH]


I'm on a dual boot with Windows XP. My current version (12.04 LTS) is an upgradation from 10.04 by liveCD. At the beginning of the upgradation Ubuntu LiveCD showed the whole HDD unallocated. To overcome the problem I first removed dmraid according to an online suggestion which didn't work. Then I used either fixparts or testdisk (or both- can't remember well). This worked and I upgraded my Ubuntu OS. I was aware at that time that Gparted showed all existing partitions including swap. Then I noticed that first one and then another Windows partition was missing. I fixed that with the help of testdisk but from then on gparted again started to show the whole HDD unallocated.

---

