---
title: "LVM showing drive full even after deleting thousands of files"
date: 2017-11-23
forum: General Help
---

### Post by Ralphie on 2017-11-23
Hello, I run Resilio Sync on my xubuntu machine, this is basically a private dropbox. It was syncing to my home dir, within an LVM partition which ran out of space completely. Things I've done:

[LIST]
[*]Moved all synced files to a new larger hard drive. 
[*]Deleted all of my synced files from the home dir. (Thousands of files, over 100GB)
[*]**[FONT=Courier New]sudo lsof | grep deleted[/FONT]** Does not show any of files that I deleted.
[*]LVM is still showing my drive to be completely full:
[/LIST]

```

$ sudo pvdisplay

  --- Physical volume ---
  PV Name               /dev/sdc3
  VG Name               xubuntu-vg
  PV Size               464.78 GiB / not usable 2.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              118984
  Free PE               0
  Allocated PE          118984

```

Any help is appreciated!
Thank you

---

### Post by Neill_R on 2017-11-23
recycle rubbish bin empty?

---

### Post by Ralphie on 2017-11-24
Thanks for the reply @Niell_R, yes trash is showing completely empty

---

### Post by Ralphie on 2017-11-24
Note, 
**df -h** shows the actual drive is only 6% used.

---

### Post by Dennis N on 2017-11-24
In that pvdisplay output, Free PE = 0 only means there is no space to create additional logical volumes, not that all the logical volumes you have are all filled up.

Suggestion:
mount all logical volumes that are in xubuntu_vg.
run 
```
df -h | grep xubuntu_vg
```
to get a better idea of what logical volume (lv) is filling up.
Example from my computer where the volume group is named os_vg:

```
dmn@Sydney:~$ df -h | grep os_vg
/dev/mapper/os_vg-ubuntu_1710    20G  5.9G   13G  33% /
/dev/mapper/os_vg-mint_mate      15G  7.1G  6.9G  51% /media/dmn/Mint-MATE
/dev/mapper/os_vg-mint_xfce      27G   15G   11G  57% /media/dmn/Mint-XFCE
/dev/mapper/os_vg-korora_gnome   15G   12G  2.1G  86% /media/dmn/Korora-GNOME
/dev/mapper/os_vg-umate_1710     27G   14G   12G  55% /media/dmn/Ubuntu-Mate-1710

```
Columns are allocated size, space used, space free, percent used.

Here, logical volume for Korora-GNOME is 86% full. Soon, I may want to expand it.

---

### Post by Ralphie on 2017-11-24
Thanks Dennis N,

The part that I was looking at for remaining space was:
```

PV Size               464.78 GiB / not usable 2.00 MiB

```

Output from suggestion did not return anything, The only thing VG related is **xubuntu--vg-root** complete **df -h**:
```

$ sudo df -h
Filesystem                    Size  Used Avail Use% Mounted on
udev                           16G     0   16G   0% /dev
tmpfs                         3.2G  9.4M  3.2G   1% /run
/dev/mapper/xubuntu--vg-root  426G   22G  384G   6% /
tmpfs                          16G   30M   16G   1% /dev/shm
tmpfs                         5.0M  4.0K  5.0M   1% /run/lock
tmpfs                          16G     0   16G   0% /sys/fs/cgroup
/dev/sdc2                     473M  187M  263M  42% /boot
/dev/sdc1                     511M  4.0K  511M   1% /boot/efi
/dev/sdb1                     932G  205G  728G  22% /media/SharedStorage
tmpfs                         3.2G   48K  3.2G   1% /run/user/1000

```

Maybe I don't have a problem? I was able to successfully run my system update just now. 
Let me know what you think of that **not usable 2.00 MiB** bit, is that just saying I can't use the last 2mb on the disk for more LVM space? 
Thanks again

---

### Post by Dennis N on 2017-11-25
PV size is the size of the partition (physical volume) when  it was created, not how much has been used. Mine show the not usable amount as well which I think is used by the file system for technical reasons, so that is normal. Based on your display, you don't have a problem with 384G available for use.

---

### Post by oldfred on 2017-11-25
Since newer drives & SSDs, partition tools have to use specific boundaries. Older partitioning did have some rounding, but you never saw it as it was less than what would be reported. Now rounding is just a bit bigger so you may have 1 or 2MB that is not usable.

Your LVM is inside a physical partition that has the 4K boundaries. Not sure if your LVM also does the same thing or not inside the physical partition.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

### Post by Ralphie on 2017-11-25
Thanks for the help everyone, so what I've learned is **df -h** is the correct way to check how much of an LVM partition is used.
Marking solved.

---

