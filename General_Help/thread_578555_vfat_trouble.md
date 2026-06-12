---
title: "vfat trouble"
date: 2007-10-17
forum: General Help
---

### Post by prow on 2007-10-17
i have a fat32 partition that is supposed to be 43.5 GB but just recently it told me that 24.7 GB are being used and that only 200MB are left.  And when i go to put a file bigger than 200MB in the partition it tells me i have no space left.

whats the deal with that?

43 - 25 = i should have 18 GB left.

---

### Post by p_quarles on 2007-10-17
Run the following commands in the terminal:
```
df -h
```
and 
```
sudo fdisk -l
```
Then paste the output here.

---

### Post by prow on 2007-10-17
```
prow@prow-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              23G  9.8G   12G  45% /
varrun                502M  296K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  136K  502M   1% /proc/bus/usb
udev                  502M  136K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   33M  469M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/disk/by-uuid/EE04F8B204F87EC1
                      5.9G  3.9G  2.1G  66% /media/windows
/dev/sda4              44G   44G  270M 100% /media/Fat32Share
/dev/sdb1              75G   54G   21G  72% /media/XData
/dev/sdc1             154G   70M  154G   1% /media/XDrive
/dev/scd0             868M  868M     0 100% /media/cdrom0

```

```
prow@prow-ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         765     6144831    7  HPFS/NTFS
/dev/sda2             766        3804    24410767+  83  Linux
/dev/sda3            3805        4047     1951897+  82  Linux swap / Solaris
/dev/sda4            4048        9729    45640665    b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10337    78147688+   7  HPFS/NTFS

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       20023   160834716    7  HPFS/NTFS

```

---

### Post by prow on 2007-10-17
its sda4

it says its using all the space but its not....there is only 25 GB worth of "stuff" in the partition

---

### Post by p_quarles on 2007-10-17
```
/dev/sda4              44G   44G  270M 100% /media/Fat32Share
```
According to this, it's actually using 44 gigs, so yes, the partition really is full. If Nautilus/Thunar/whatever-file-manager is telling you it's using 25 gigs, this is probably the effect of fragmentation and the gross inefficiency of the FAT32 filesystem.

---

### Post by maybeway36 on 2007-10-17
I wonder if some Linux developer will eventually add exFAT support?

---

### Post by prow on 2007-10-17
what if i move all my data to my external drive and format the partition to NTFS...will i be able to use the full 44GB then?
with ntfs-3g of course

---

### Post by prow on 2007-10-17
and i've also noticed my ntfs second hard drive "XData" is only using 36.7 GB but its saying its using 54GB....this cant be due to fragmentation can it?   is there anyway to defrag a fat32 or an ntfs in linux?

---

### Post by p_quarles on 2007-10-17
> **prow said:**
> and i've also noticed my ntfs second hard drive "XData" is only using 36.7 GB but its saying its using 54GB....this cant be due to fragmentation can it?   is there anyway to defrag a fat32 or an ntfs in linux?
I understand that there are ways, but they aren't as reliable or safe as using the Windows defrag tool. I would just boot into Windows, take a look at what *it* says you're using on those partitions, and defrag if need be.

---

### Post by prow on 2007-10-17
> **p_quarles said:**
> I understand that there are ways, but they aren't as reliable or safe as using the Windows defrag tool. I would just boot into Windows, take a look at what *it* says you're using on those partitions, and defrag if need be.

ok, thats what i was about to do anyway.  Thanks!

---

### Post by prow on 2007-10-17
ok so i figured out the problem....
each partition creates its own hidden trash directory.  The trash in each partition was huge.  Is there anyway to link the trash from each partition to the empty trash function on the root file system partition?

---

### Post by p_quarles on 2007-10-17
lol ... that makes more sense than fragmentation.

To your question: I doubt it. The trash function in Linux is part of the GUI, and so is separate from the actual workings of the filesystem. In Windows, on the other hand, the filesystem and GUI are more tightly integrated, so it makes sense that the trash function actually works as part of the filesystem. (for the record: this could be wrong; I don't use Windows often enough to know any of this for sure)

From the sound of it, you don't use Windows very often yourself, and are accessing these partitions mainly from Linux. If that's the case, I would consider formatting one or part of one as an ext3 data partition, and moving everything you use frequently to that. 

Of course, you can always just nuke files by using the "rm" command, and they will completely disappear. This can be relatively dangerous, though (i.e., a typo can remove everything).

---

### Post by prow on 2007-10-18
thanks for the tips....

I actually use this machine mostly for a media server so that would explain the many partitions...i rarely use files on the machine its self so a bigger ext3 partition would be useless for me

i'll just stick to being careful about how i remove my files....i do frequent backups too so im not nervous

im also having trouble with another issue..maybe you can help me out....

[http://ubuntuforums.org/showthread.php?t=580289](http://ubuntuforums.org/showthread.php?t=580289)

---

