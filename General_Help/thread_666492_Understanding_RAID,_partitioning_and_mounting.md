---
title: "Understanding RAID, partitioning and mounting"
date: 2008-01-13
forum: General Help
---

### Post by erkswede on 2008-01-13
Hello all

I'm trying to understand what I'm doing ;-) I have a Ubuntu 7.04 server up and running. Today I have added two new discs, 320 GB IDE and my intention were to setup a RAID 1 array. My MB is an older MSI 845 Ultra with the Promise pdc20276 RAID controller which I have enabled in BIOS. I have also set up a RAID 1 array with the two discs in the controllers BIOS.

After booting ubuntu I thought I had to use dmraid to activate the array. Got an error that this already was done :)

dmraid -r:
```
/dev/sdb: pdc, "pdc_bhbfahjig", mirror, ok, 625000000 sectors, data@ 0
/dev/sdc: pdc, "pdc_bhbfahjig", mirror, ok, 625000000 sectors, data@ 0
```

I then used fdisk to partition the array:
```
fdisk /dev/mapper/pdc_bhbfahjig
...
Command (m for help): p

Disk /dev/mapper/pdc_bhbfahjig: 320.0 GB, 320000000000 bytes
255 heads, 63 sectors/track, 38904 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_bhbfahjig1               1       38904   312496348+  83  Linux

```
(Actually there were two partitions in HPFS/NTFS format which I deleted. I'm guessing they appeared after the BIOS array setup? )

I then made a mistake and tried to format /dev/mapper/pdc_bhbfahjig which resulted in the following
```

mkfs.ext3 /dev/mapper/pdc_bhbfahjig
mke2fs 1.40-WIP (14-Nov-2006)
/dev/mapper/pdc_bhbfahjig is apparently in use by the system; will not make a filesystem here!
```

I also tried to mount it:
```
mount /dev/mapper/pdc_bhbfahjig /test
mount: /dev/mapper/pdc_bhbfahjig already mounted or /test busy

```

I guess the formatting and the mounting should have been done on /dev/mapper/pdc_bhbfahjig1 (please notice the"1" at the end).

I was very confused when reading various guides on this subject. I didn't notice that formatting and mounting should be done on the partition in the array, and not on the array itself. Is this a correct interpretation of what has happened?

Also confusing when one can see both the array and the partition in dev/mapper:
```
ls /dev/mapper
control  pdc_bhbfahjig  pdc_bhbfahjig1
```

Now, does all this make any sense to someone who, in contrast to myself, knows what they are doing?
And, is there anything faulty with my setup that I haven't noticed or done wrong.

Thanks
/Erik

---

### Post by fjgaude on 2008-01-13
Have you had time to look at this link:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Might help.

---

### Post by erkswede on 2008-01-13
Yes I have and yes it did help a lot, thanks.

---

### Post by fjgaude on 2008-01-13
Let us know if you have issues...

---

