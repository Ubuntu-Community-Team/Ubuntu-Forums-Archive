---
title: "External HDD clean and file system change, fdisk etc issues"
date: 2014-11-13
forum: General Help
---

### Post by apple6 on 2014-11-13
Hi, I know that this is a pretty straight forward thing to do in Gparted, but I'm trying to use the terminal on it instead. 

What I want to do is - 

[LIST]
[*]Clean the drive (I'm not bothered about it being forensically spotless - an rm -rf * would do really)
[*]Change it from an NTFS drive to an ext4 drive. 
[/LIST]

I've spent ages on this, but I can't figure out what I'm meant to do; heres what I'm doing so far...

Connect the drive - check where it is with ```
mount
```

```
/dev/sdb1 on /media/vco/MiniMe type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)



```

So it's on /dev/sdb1

I then unmount it using 

```
umount /dev/sdb1

```


So the drive is connected, but unmounted. 

I then use fdisk with the following command - 

```
sudo fdisk /dev/sdb
```

This brings up the fdsik prompt - I want to delete the partition on it. (Not sure whether it's logical or primary...) 

So I enter 'd' for the delete partition command

I get the following error message though 
```

Command (m for help): d
No partition is defined yet!


Command (m for help): 

```
I don't know what's this referring to - ***I've entered the drive that I want fdisk to act on, so what's the problem?*** 

Googling this seems to imply that I need to have the partition visible in fdisk -l when I start all this, [I][B]so I need to have it Mounted when I delete it? 

[/B][/I]So I mount the drive and go back to fdisk. 

fdisk -l shows the drive now, here's the info from that : 

```
Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd7f7850d


   Device Boot      Start         End      Blocks   Id  System
Note: sector size is 4096 (not 512)

```

Not sure what the *Note: sector size *is referring to here, something to do with where the partition starts? Dunno... anyway




So I start up fdisk again with the same command 

```
sudo fdisk /dev/sdb
```


I want to delete a partition so I press 'd'

AGAIN, I get 
```

No partition is defined yet!



```

I've no idea what this means. 

If I unmount the drive and then go through the fdisk process I get the following screen (when trying to print out the partitions for that drive) 
```

Command (m for help): p


Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd7f7850d


   Device Boot      Start         End      Blocks   Id  System


Command (m for help): 

```


So, I found a link on this form which [led me to this page]("http://www.pendrivelinux.com/usb-x-ubuntu-610/")

I followed the steps in there, here they are - 
```

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd7f7850d


   Device Boot      Start         End      Blocks   Id  System


Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 
Using default value 1
First sector (2048-976773166, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-976773166, default 976773166): 
Using default value 976773166


Command (m for help): p


Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd7f7850d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976773166   488385559+  83  Linux


Command (m for help): w
The partition table has been altered!


Calling ioctl() to re-read partition table.
Syncing disks.



```

The part about umounting the drive after this process didn't seem necessary - as I couldn't see the drive anyway. 



Here's what I have from mount  :

```


vco@geoHP:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda9 on /home type ext4 (rw)
/dev/sda2 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=vco)
/dev/sdc1 on /media/vco/BlackBox type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)




```

If I try and click on the drive in the GUI I now get this error 

[IMG]https://lh3.googleusercontent.com/eUt-py237rDljFNZIVdAbBHSUWGNHuu-27x96gvcg4v0=w420-h218-no[/IMG]




[Apparently this is a solution]("https://bbs.archlinux.org/viewtopic.php?id=140456") - but it doesn't mean anything to me. 

I'm kind of burnt out at this point and would really appreciate some help

Cheers

---

### Post by oldfred on 2014-11-13
Sometimes just unplugging it and replugging it in works as now it is seen as a totally different device.
Did you label it MiniMe or was that the old NTFS partition which does not exist, so it cannot mount it.

If your system is UEFI (you show an efi partition), you should use gdisk and partition drive as gpt not MBR(msdos). The fdisk program does not work on gpt partitioned drives. You can also use parted from command line, but I have only used gparted for years.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

If formatted as ext4, you will also have to give yourself ownership & permissions to use it.
      
 [URL="https://help.ubuntu.com/community/FilePermissions"]https://help.ubuntu.com/community/FilePermissions


[/URL]

---

