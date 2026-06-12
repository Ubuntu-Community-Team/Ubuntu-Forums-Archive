---
title: "Where did Partitions Go?"
date: 2013-12-20
forum: General Help
---

### Post by Rick St. George on 2013-12-20
Apparently after some update, Now looking into FILE SYSTEM, I don't see my other partitions! I used to access them on this 500GB drive, now I only see the 48 +/- GB Ubuntu partition. 

How do I get this ability back?

EDIT: Added the following Output (bootinfoscript)

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 9046999 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       (,msdos1)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   486,560,654   486,560,592  83 Linux
/dev/sda2         486,560,655   488,392,064     1,831,410   5 Extended
/dev/sda5         486,560,718   488,392,064     1,831,347  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        f8d48b01-dfc2-49ef-b196-9f3ab3c7c00f   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================


Thanks,
Rick

---

### Post by jfolsom2 on 2013-12-20
Do you only have one HD in your machine? According to what you posted, this is a 250GB Hard Drive, not 500GB. It has 1 Primary partition (With linux) And 1 Extended Partion that is being used for swap.  There doesn't appear to be anything else there to browse to.

From the terminal, please post the output of:
```

sudo fdisk -l

```

---

### Post by Rick St. George on 2013-12-26
Sorry, I must have been thinking of another computer. It does have another HDD. Removed that SATA to use in a laptop. Tried to update to Newer LTS, but system never recovered. Its the one with SIS video and can't find a solution. Posted at [http://ubuntuforums.org/showthread.php?t=2194434](http://ubuntuforums.org/showthread.php?t=2194434)
Will consider / make this solved / closed.

---

