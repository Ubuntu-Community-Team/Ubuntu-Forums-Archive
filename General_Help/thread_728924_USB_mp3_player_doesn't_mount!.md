---
title: "USB mp3 player doesn't mount!"
date: 2008-03-19
forum: General Help
---

### Post by grazzt_85 on 2008-03-19
I have an MP3 Player (ZicPlay Microkey 1 GB) that was mounting normally, but it stopped mounting some day. I plug it on now but nothing happens! Other USB devices are working properly.

These are the outputs of gedit /etc/fstab and fdisk -l in case they are needed for the solution

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03569fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           38769       38899     1052257+  82  Linux swap / Solaris
/dev/sda2            2678       38768   289900957+   7  HPFS/NTFS
/dev/sda3   *          33        2677    21245962+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00008ed2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      775218   390709840+   7  HPFS/NTFS

```

```
proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=b18c1aa6-e2f6-49b7-91a0-0453809973d2 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda2 :
UUID=6832D0AD32D0818C /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sdb1 :
UUID=0A58AC7658AC61E5 /media/sdb1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda1 :
UUID=bf38c943-f777-4ded-9751-bc1878a2c51c none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hda /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
```

---

### Post by vahnx on 2008-03-19
Does it say unclean shutdown when you plug it in? Or any error dialogue? I know in ubuntu you have to right click a volume and unmount it or 50% of the time it won't remount unless you force it with a command like,

eg: This is what I do when I unplug my external and it won't remount when I plug it back in:
```
sudo mount -t ntfs-3g /dev/sdb1 /media/External -o force
```

---

### Post by grazzt_85 on 2008-03-19
I tried that command but the problem is that the device isn't even shown on /dev directory.

THe only thing that shows that the usb is seen is a log (i don't remember the command, i found it somewhere here) at the command that says usb is plugged

---

