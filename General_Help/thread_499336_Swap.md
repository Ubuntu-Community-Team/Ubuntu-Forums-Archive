---
title: "Swap"
date: 2007-07-12
forum: General Help
---

### Post by malfist on 2007-07-12
Can I remove the swap partition and force ubuntu to use my RAM? The swap seems to be causeing problems with my partition table and I have a gig of RAM so it might be better to remove it. How can I do this?

---

### Post by dannyboy79 on 2007-07-12
I don't see what you mean that the swap is causing problems with your partition table? BUT to turn swap off, simply issue 

sudo swapoff -a

If that doesn't  turn it off, then read up on "man swapon" to see what it says about stopping it per the device (/dev/hda4) instead of having swapoff parse your fstab file.

then check to make sure it's not being used anymore

free

then you can delete that partition and recreate it but I can tell you that 1gb is not that much ram anymore especially with Compiz or Beryl, gogle earth, video encoding etc etc. I would use swap if I were you. Set it to 512mb. Good luck

---

### Post by malfist on 2007-07-12
FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap is waht I'm getting with cfdisk.
My partition table (which isn't working right) is this:
```

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63        9169    73151977+   7  HPFS/NTFS
/dev/hdc2           13880       24321    83875365    f  W95 Ext'd (LBA)
/dev/hdc3           10665       13879    25824487+  83  Linux
/dev/hdc5           14025       24321    82710621    7  HPFS/NTFS
/dev/hdc6           13880       14024     1164649+  82  Linux swap / Solaris

```

---

### Post by dannyboy79 on 2007-07-12
> **malfist said:**
> FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap is waht I'm getting with cfdisk.
My partition table (which isn't working right) is this:
```

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63        9169    73151977+   7  HPFS/NTFS
/dev/hdc2           13880       24321    83875365    f  W95 Ext'd (LBA)
/dev/hdc3           10665       13879    25824487+  83  Linux
/dev/hdc5           14025       24321    82710621    7  HPFS/NTFS
/dev/hdc6           13880       14024     1164649+  82  Linux swap / Solaris

```


yeah, that's VERY BAD!!!!!! According to your partition table, your linux partition doesn't even start AFTER the extended partition which is very bad. I would use TestDIsk from the gparted livecd to redo your partition table. It's not just partition 6, at least not by looking at this view anyway! I would strongly suggest you actually use a live cd, back anything important up, then actually write zero's to the disk (this will wipe all data from it) then start over. that's just my opinion but testdisk should be able to fix your partition table for you!

---

### Post by malfist on 2007-07-12
****, that's not what I want to hear, my drive is basically full (200GB) :( and I can't access the windows partition right now because I used fdisk to try and fix it and set it's filetype to 7 and nothing else can see it as that :(

---

### Post by malfist on 2007-07-12
Testdisk shows this:
```

Disk /dev/hdc - 200 GB / 186 GiB - CHS 24321 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors
Invalid NTFS boot
 1 * HPFS - NTFS             62   0  1 10663 254 63  170321130
 1 * HPFS - NTFS             62   0  1 10663 254 63  170321130
 2 E extended LBA         13879   0  1 24320 254 63  167750730
 3 P Linux                10664   0  1 13878 254 63   51648975
 5 L HPFS - NTFS          14024   1  1 24320 254 63  165421242 [Backup]
   X extended             13879   0  2 14023 254 63    2329424
 6 L Linux Swap           13879   2  1 14023 254 63    2329299

```

I've been getting help on the partition table here: [http://ubuntuforums.org/showthread.php?t=496126](http://ubuntuforums.org/showthread.php?t=496126)

---

