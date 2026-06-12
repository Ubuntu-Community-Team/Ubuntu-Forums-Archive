---
title: "Mounting an old LUKS-encrypted boot disk"
date: 2015-01-04
forum: General Help
---

### Post by ofnuts on 2015-01-04
After successful installation of 14.04 on a new HDD (with LUKS encryption), I put my previous 12.10 boot HDD (also LUKS-encrypted) in a USB enclosure and connected it.

I tried the easy solution first: KDE asks me for a password, but that fails, so trying the hard way (assume 'sudo' at the right places below):

[LIST]
[*]prepare mount point: 'mkdir /mnt/old' 
[*]using partitions manager, I see the 300GB disk  as 250MB sdd1 (pirmary) and a 293GB sdd2 that further contains an sdd5. 
[*]'cryptsetup -v luksOpen /dev/sdd5 old': command successful 
[*]'cryptsetup status old':```
/dev/mapper/old is active.
  type:    LUKS1
  cipher:  aes-xts-plain64
  keysize: 512 bits
  device:  /dev/sdd5
  offset:  4096 sectors
  size:    624635904 sectors
  mode:    read/write

``` 
[*]'mount /dev/mapper/old /mnt/old' ```
mount: unknown filesystem type 'LVM2_member'
``` 
[*]of course 'dpkg -s lvm2' says that the lvm2 package is installed 
[/LIST]

What am I missing?

---

