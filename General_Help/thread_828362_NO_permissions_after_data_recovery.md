---
title: "NO permissions after data recovery"
date: 2008-06-13
forum: General Help
---

### Post by TheAJKMan on 2008-06-13
[This is the link]("http://ubuntuforums.org/showthread.php?t=828231") the problem underneath stems from.

Okay, after a day filled with much drama, I've managed to get a working installation of Ubuntu gain. I've followed various bits of advice trying to recover/mount my second hdd and finally seem to have gotten it right following advice in this thread. The problem is that when I try to go into the various directories, I get this error message ....."**The Folder contents could not be displayed. You do not have the permissions necessary to view the contents of "recup_dir.xxx**" How do I set it up that I get those permissions as I'd like to recover as much of the data that is in those directories as is possible.

Hope you guys can help the newb yet again. Thanks.

---

### Post by Rocket2DMn on 2008-06-13
Can you please post the output of:
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
Also, if you can identify which device/partition we are dealing with, that would be great.

---

### Post by TheAJKMan on 2008-06-13
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76197a10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80004020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris

---

### Post by TheAJKMan on 2008-06-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0032a34-1b53-4f31-8a1d-6512c4aefcb2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=46581436-af07-405b-9003-5571dd0d76e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sdb1
/dev/sdb1 /media/data ext3 defaults,user 0 2

---

### Post by TheAJKMan on 2008-06-13
/dev/sda1: UUID="a0032a34-1b53-4f31-8a1d-6512c4aefcb2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="46581436-af07-405b-9003-5571dd0d76e8" 
/dev/sdb5: TYPE="swap" UUID="ed0c4100-a41a-4fbe-a88f-994c991baff1" 

AND....

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

---

### Post by Rocket2DMn on 2008-06-13
Is /dev/sdb1 an old install that you are trying to recover from?  Do you have the same username in this install?  You can try adding "umask=000" to the options column of your fstab file and get right of the "user" option.  Don't forget to remount the drive (doesn't look like it's mounted at the moment).

Alternatively, if you are sure you will never try and boot from that drive again, you can chown the entire partition with your username.  If you choose this option, be sure not to do it on your local filesystem and be sure that you won't be trying to boot from that drive again, because it won't work.

---

### Post by TheAJKMan on 2008-06-13
How do I use the chown and unmask commands. Please bear with me as I'm pretty much a newb at linux. 

Thanks

---

### Post by Rocket2DMn on 2008-06-13
In order to chown a partition, you run
```
sudo chown -R <your_username> /media/<mount_point>
```
In your case, for /dev/sdb1 which is mounted at /media/data, you would make sure the partition is mounted, then use the chown command (this works because it is an ext3 filesystem, not FAT32 or NTFS)
```
sudo mount -a
sudo chown -R <your_username> /media/data
```
Again, that can't be undone, so I prefer to try the umask first:
Open /etc/fstab for editing
```
gksudo gedit /etc/fstab
```
Change the last line from
```
/dev/sdb1 /media/data ext3 defaults,user 0 2
```
to
```
/dev/sdb1 /media/data ext3 defaults,umask=000 0 2
```
Then run
```
sudo umount /dev/sdb1
sudo mount -a
```
If any of those commands spit output, please post it here with the command included.  With umask in place you should be able to access the drive.

---

### Post by TheAJKMan on 2008-06-14
Errr, I presume you meant something like this.....

[B]theajkman@theajkman-desktop:~$ gksudo gedit /etc/fstab
theajkman@theajkman-desktop:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted
theajkman@theajkman-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

theajkman@theajkman-desktop:~$ 
[/B]

---

### Post by Rocket2DMn on 2008-06-14
OK, sounds like something may be wrong with your sdb1 partition since it didn't show up in the blkid command and it won't let you mount.  Let's run a file system check on it.
```
sudo fsck /dev/sdb1
```
Then try to remount the drive. Please post the results of fsck and the mount attempt.

---

