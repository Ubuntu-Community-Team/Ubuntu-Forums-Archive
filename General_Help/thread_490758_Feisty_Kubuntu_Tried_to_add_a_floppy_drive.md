---
title: "Feisty Kubuntu Tried to add a floppy drive"
date: 2007-07-02
forum: General Help
---

### Post by cat_herder_5263 on 2007-07-02
This is on a computer I built several days ago. New case & motherboard, other components taken from a 3-year old computer that died. I pre-partitioned the disk with Partition Commander to set it up for dual booting with Win98SE (don't ask:twisted:). Created the following partitions: 
```

/dev/hda1   FAT32 win98SE C:   ~  6GB
/dev/hda2 <extended partition for remainder of drive>
/dev/hda5   FAT32 win98SE D:   ~ 12GB
/dev/hda6   swap               ~  4GB
/dev/hda7   ext3  /            ~ 40GB
/dev/hda8   ext3  /usr/local   ~ 40GB
/dev/hda9   ext3  /home        ~180GB

```
Installed Kubuntu 7.04 into the extended partitions. Installed a few essential apps that weren't included in Kubuntu and played with the configuration, tweaking KDE to work the way I prefer. I was **very** happy.:D
Yesterday I decided to put a floppy drive on the system. Like a fool, I went to the "System Settings" Disk&Filesystems app and tried to add the floppy using the "New" button. I must have done something **REALLY STUPID** because it hung for a long time and appeared to do absolutely nothing. Now the System Settings app shows this partition scheme:
```

1 Partition 5.9 Gb   /media/hda1    vfat  /dev/hda1   enabled
2 Partition 1.0 Kb   /proc          proc  proc        enabled
5 Partition 11.7 Gb  /media/hda5    vfat  /dev/hda5   enabled
6 Partition 3.9 Gb   none           swap  /dev/hda6   enabled
7 Partition 39.1 Gb  /media/hda6    ext3  /dev/hda7   enabled
8 Partition 39.1 Gb  /media/hda7    ext3  /dev/hda8   enabled
9 Partition 179.8 Gb /media/hda8    ext3  /dev/hda9   enabled

```
fdisk shows exactly what I'd expect:
```

   Device Boot Start    End     Blocks   Id  System
/dev/hda1          1    765    6144831    b  W95 FAT32
/dev/hda2        766  36481  286888770    f  W95 Ext'd (LBA)
/dev/hda5        766   2295   12289693+   b  W95 FAT32
/dev/hda6       2296   2805    4096543+  82  Linux swap / Solaris
/dev/hda7   *   2806   7904   40957686   83  Linux
/dev/hda8       7905  13003   40957686   84  Linux
/dev/hda9      13004  36481  188587003+  83  Linux

```
I can't figure out how to fix this. I'm sure it's just a weird display problem, but it really bothers me.

I manually added a floppy entry exactly like the one in my SuSE 9.3 fstab
```
/dev/fd0   /media/floppy  subfs  noauto,fs=floppyfss,procuid,nodev,nosuid,sync 0 0
```
But Feisty doesn't like fstype. It doesn't like msdos or umsdos either. Can anybody suggest an /etc/fstab entry that will work for Feisty?

---

### Post by confused57 on 2007-07-02
Maybe an entry similar to this in fstab would work:
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

You may need to first make a directory to mount it to:
```
sudo mkdir /media/floppy0
```

---

### Post by cat_herder_5263 on 2007-07-03
Thanks, that worked. :KS

Any ideas on the SystemSettings|Disk&Filesystems display problem?

ANYONE?

---

### Post by Detonate on 2007-07-03
You might want to read this thread over on the Kubuntu forum.

[http://kubuntuforums.net/forums/index.php?topic=3081029.0](http://kubuntuforums.net/forums/index.php?topic=3081029.0)

---

