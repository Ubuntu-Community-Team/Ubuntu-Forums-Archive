---
title: "[SOLVED] mounting problems for sda1 has effected my windows partition"
date: 2008-04-01
forum: General Help
---

### Post by harryliddic on 2008-04-01
I have been trying for two days to mount sda1, following instructions faithfully, now I go back to my window 2000 partition in grub and windows won't let me in. I have important work that needs completion on the windows side and I cant get there physically or through wine.

---

### Post by Rocket2DMn on 2008-04-01
Can you post the output of
```
sudo fdisk -l
cat /etc/fstab
mount -a
```

---

### Post by harryliddic on 2008-04-01
yes here it is

harry@harry-desktop:~$ sudo fdisk -l
[sudo] password for harry:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60466447

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        9484    37110150   83  Linux
/dev/sda3            9485        9729     1967962+  82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031306752 bytes
32 heads, 63 sectors/track, 999 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0xedba4c3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         969      976562+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2             970         999       30240   82  Linux swap / Solaris
harry@harry-desktop:~$ 


harry@harry-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=05cd73b0-8103-4e6a-8685-8b494ede9871 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6AE45588E4555801 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=a5bf7916-dee5-4eb0-b81a-81bec1ee1906 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
harry@harry-desktop:~$ 


harry@harry-desktop:~$ mount -a
mount: only root can do that
harry@harry-desktop:~$ sudo mount -a
Failed to access '/dev/disk/by-uuid/6AE45588E4555801': No such file or directory
harry@harry-desktop:~$ 


there it is, I pray you can make sense of it

---

### Post by Rocket2DMn on 2008-04-01
OK, it seems Ubuntu changed how it recognizes your hard drives, can you also post the output of
```
ls -l /dev/disk/by-uuid/
```
It seems the UUID of your ntfs partition changed, too.  Once I have the info from that command, I will help you edit fstab so the partitions mount correctly.
Also, what exactly happens when you try to boot into windows?

---

### Post by harryliddic on 2008-04-01
I get an error msg 13: no executable file

---

### Post by Rocket2DMn on 2008-04-01
Well that isn't good, you may need to try and fix your windows partition from the windows cd.  However, we should be able to mount it in linux, but I would still like the output of that ls command so we can mount it with the appropriate UUID in fstab (rather than using the more unstable /dev location).

---

### Post by harryliddic on 2008-04-01
i forgot this

harry@harry-desktop:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-04-01 02:45 05cd73b0-8103-4e6a-8685-8b494ede9871 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-04-01 02:45 a5bf7916-dee5-4eb0-b81a-81bec1ee1906 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-04-01 09:46 ca6bce26-6b6d-4ed1-9cfd-6215ea2fafda -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-04-01 02:45 ebba4ce4-b6b5-4c7d-af1a-1a779ebe5f61 -> ../../sda1
harry@harry-desktop:~$

---

### Post by Rocket2DMn on 2008-04-01
OK, we're going to make a backup of your fstab, then open it for editing
```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
Then replace this line:
```
# /dev/hda1
UUID=6AE45588E4555801 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
with this line:
```
# /dev/sda1
UUID=ebba4ce4-b6b5-4c7d-af1a-1a779ebe5f61 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
Save and close. Now make the new mount point, then mount:
```
sudo mkdir /media/windows
sudo mount -a
```
If any errors show up, post them here.  This may not help you get into windows, but you can at least copy your data over to back it up in the case that you have to reinstall windows.
You may need to enable writing to the drive using Applications->System Tools->NTFS Configuration Tool

---

### Post by harryliddic on 2008-04-01
I got this

harry@harry-desktop:~$ sudo mount -a
mount: unknown filesystem type 'locale=en_US.utf8'
harry@harry-desktop:~$

---

### Post by Rocket2DMn on 2008-04-01
Bah, sorry I forgot the filesystem column, I updated my entry above, the new line should look like this:
```
# /dev/sda1
UUID=ebba4ce4-b6b5-4c7d-af1a-1a779ebe5f61 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
Also, this April Fools color theme on the forum is very distracting...

---

### Post by harryliddic on 2008-04-01
i got this

harry@harry-desktop:~$ sudo mount -a
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
harry@harry-desktop:~$

---

### Post by harryliddic on 2008-04-01
two nights ago someone suggest i use a command that was something like **mkse** and someone responded that changes files to ext3 or was close to that command. I can look it up for you. I got a doctor's appointment and will be gone for two hours or so, I pray to god you will be around when I get back.

---

### Post by Rocket2DMn on 2008-04-01
OK, try just straight up
```
sudo mount -t ntfs-3g /dev/sda1 /media/windows
```
I expect you will get the same error, in which case you should try installing ntfsprogs so we can try to fix the partition
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
Then try to mount again
```
sudo mount -a
```
(or the other mount command above)

If this fails to fix the problem, it seems your partition is terribly corrupted - did you try resizing it or something?  You will have to try and use the windows disc to recover the partition, because there isn't really anything else we can do with ntfs drives using linux.

---

### Post by harryliddic on 2008-04-02
It has taken all night to format my windows partition and put the software back on. I came back to linux and tried **sudo mount -a **and got this response


harry@harry-desktop:~$ sudo mount -a
Failed to access '/dev/disk/by-uuid/ebba4ce4-b6b5-4c7d-af1a-1a779ebe5f61': No such file or directory
harry@harry-desktop:~$ 

I know now the my ntfs system was corrupted but everthing is back on track on that side now if I can just mount sda1 on this side i'll be content. I'm sending you a preemptive thanks for all your work.

---

### Post by Rocket2DMn on 2008-04-02
No problem, it's possible the UUID changed when you reformatted the partition, so please post the output of these commands again:
```
sudo fdisk -l
cat /etc/fstab
ls -l /dev/disk/by-uuid/
```
Then we can get fstab correct.

---

### Post by harryliddic on 2008-04-02
here it comes again

harry@harry-desktop:~$ sudo fdisk -l
[sudo] password for harry:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60466447

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        9484    37110150   83  Linux
/dev/sda3            9485        9729     1967962+  82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031306752 bytes
32 heads, 63 sectors/track, 999 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0xedba4c3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         969      976562+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2             970         999       30240   82  Linux swap / Solaris
harry@harry-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#proc            /proc           proc    defaults        0       0
# ext/dev/hda2
UUID=05cd73b0-8103-4e6a-8685-8b494ede9871 /               3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=ebba4ce4-b6b5-4c7d-af1a-1a779ebe5f61 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
# /dev/hda3
UUID=a5bf7916-dee5-4eb0-b81a-81bec1ee1906 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
harry@harry-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-04-02 03:47 05cd73b0-8103-4e6a-8685-8b494ede9871 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-04-02 03:47 4274088174087A45 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-02 03:47 a5bf7916-dee5-4eb0-b81a-81bec1ee1906 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-04-02 10:48 ca6bce26-6b6d-4ed1-9cfd-6215ea2fafda -> ../../sdb2
harry@harry-desktop:~$

---

### Post by Rocket2DMn on 2008-04-02
OK, we're gonna edit fstab again
```
gksudo gedit /etc/fstab
```
Change the line
```
# /dev/sda1
UUID=ebba4ce4-b6b5-4c7d-af1a-1a779ebe5f61 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
to
```
# /dev/sda1
UUID=4274088174087A45 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
or alternatively change it to just
```
# /dev/sda1
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
Save and close, then
```
sudo mount -a
```
That should get you back in business, otherwise post any error outputs.

---

### Post by harryliddic on 2008-04-02
NO ERROR MESSAGES! success? I will find out after I go to an appointment at 2:00. many thanks, your expertise is vast and amazing. May you and yours live 200 years.

---

