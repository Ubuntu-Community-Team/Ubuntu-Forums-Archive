---
title: "How to backup an external hard drive?"
date: 2014-06-29
forum: General Help
---

### Post by ron177 on 2014-06-29
Dear all,
 What is the quickest way to backup an external hard drive? I have an  external hard drive that I need to back up. So I went and purchased a  second external drive. I formatted the latter but I have forgotten how  to do this through rsync. Can someone help me?
 I put the following command line but it didn't work:
 rsync -ruv --delete /media/Extension /media/Backup
 "Extension" is the name of my first hard drive which serves as an  extension of my internal hard drive. "Backup" on the other hand is the  second external hard drive.
 Can someone help me with this?

 R

---

### Post by Bucky Ball on 2014-06-29
I generally use Clonezilla. Here's some light reading:

[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

---

### Post by oldfred on 2014-06-29
Are those the names/labels of the external drives or the actual mount points when mounted? 

Type these:
mount
sudo blkid
sudo parted -l

       [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[URL="http://ubuntuforums.org/showthread.php?t=1883834"]http://ubuntuforums.org/showthread.php?t=1883834
[/URL]
 Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

One of my commands, but both mounts exist at time I run this:
rsync -aruvlP /mnt/data/Documents /mnt/backup


[URL="http://ubuntuforums.org/showthread.php?t=1883834"]
[/URL]

---

### Post by ron177 on 2014-06-29
I typed "mount" and this is the result:

rk@rk-Satellite-C55D-A:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=rk)
/dev/sdc1 on /media/rk/Backup type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdd1 on /media/rk/Extension type ext4 (rw,nosuid,nodev,uhelper=udisks2)
rk@rk-Satellite-C55D-A:~$

---

### Post by ron177 on 2014-06-29
And here's the response for the second command:

rk@rk-Satellite-C55D-A:~$ sudo blkid
[sudo] password for rk: 
/dev/sda1: UUID="4D17-243F" TYPE="vfat" 
/dev/sda2: UUID="5c7cddd9-af38-4e5f-a091-32cd4c7d03f3" TYPE="ext4" 
/dev/sda3: UUID="d538ddf0-9e35-45ed-8434-a81e33396039" TYPE="swap" 
/dev/sdc1: LABEL="Backup" UUID="045ddf09-bf7e-440a-a505-79b48786ba11" TYPE="ext4" 
/dev/sdd1: LABEL="Extension" UUID="59480fbc-7044-441c-8d77-b41387b976fd" TYPE="ext4" 
rk@rk-Satellite-C55D-A:~$ ^C
rk@rk-Satellite-C55D-A:~$

---

### Post by ron177 on 2014-06-29
And here's the result for the third command:

rk@rk-Satellite-C55D-A:~$ sudo parted -l
Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  538MB  537MB   fat32                 boot
 2      538MB   496GB  496GB   ext4
 3      496GB   500GB  3705MB  linux-swap(v1)


Model: WD My Book 1230 (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  3001GB  3001GB  primary


Model: Toshiba External USB HDD (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  1000GB  1000GB  ext4               msftdata


rk@rk-Satellite-C55D-A:~$

---

### Post by oldfred on 2014-06-29
This is the path you show.

rsync -aruvlP --delete /media/rk/Extension /media/rk/Backup

If you have not set ownership & permissions you must do that first.
       sudo chmod -R a+rwX,o-w /media/rk/Backup
 sudo chown -R $USER:$USER /media/rk/Backup

---

### Post by yancek on 2014-06-29
> rsync -ruv --delete /media/Extension /media/Backup

Your initial post shows the above command whereas your last post shows "rk" between media and Extension/Backup.  That would account for the failure unless that was a typo in your initial post.  Also, you say it "didn't work" which is pretty vague.  What exactly happened?  Any messages?  warnings?  error output?

---

