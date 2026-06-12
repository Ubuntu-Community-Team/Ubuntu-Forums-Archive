---
title: "NTFS Drives are Read Only in Ubuntu 13.04"
date: 2013-05-05
forum: General Help
---

### Post by Mesopotamia on 2013-05-05
Dear all,

I have been facing two problems with 13.04:

1. Internal HDD don't mount automatically, and when I modify them
2. They mount automatically but they're mounted as Read-only.

I tried using NTFS, and NTFS-3g in the fstab file but they still mount at read only (i.e. I can't move them to the trash nor renaming them).

The same fstab I used to use with 12.04 and it was working fine.

Your help is very much appreciated.

---

### Post by slimline66 on 2013-05-05
Hello Mesopotamia,

I have a similar problem except it is a ext4 partition that mounts as read only, my ntfs has full rw permissions when mounted.

If it helps, this is the line from my fstab that automounts my ntfs partition.
> /dev/disk/by-uuid/A4B0266BB0264460 /media/Data auto nosuid,nodev,nofail,x-gvfs-show 0 0

I'm on 13.04 too. ;)

---

### Post by Morbius1 on 2013-05-05
Please post the output of the following commands:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
mount
```
And if it's not too late stay away from the "Disks" utility. It's not ready for prime time and adds options like "nofail,x-gvfs-show" which just causes more problems.

---

### Post by slimline66 on 2013-05-05
> And if it's not too late stay away from the "Disks" utility. It's not  ready for prime time and adds options like "nofail,x-gvfs-show" which  just causes more problems.lol yes I found that out. Bootup stalled at mounting my ext4 partition with those two options. Once removed it mounted more or less ok. The ntfs partition mounts ok with them though!

---

### Post by slimline66 on 2013-05-05
You might want to try this Mesopotamia, it worked for me:
[http://ubuntuforums.org/showthread.php?t=2142284&p=12634271#post12634271](http://ubuntuforums.org/showthread.php?t=2142284&p=12634271#post12634271)

---

### Post by Morbius1 on 2013-05-05
> **slimline66 said:**
> You might want to try this Mesopotamia, it worked for me:
[http://ubuntuforums.org/showthread.php?t=2142284&p=12634271#post12634271](http://ubuntuforums.org/showthread.php?t=2142284&p=12634271#post12634271)
Can't do a chown or chmod on a mounted ntfs partition since there are no Linux ownership / permissions bits within a Windows filesystem. To change ownership / permissions on an ntfs partition you need to change it within the mount command itself.

Something like the NTFS template:
```
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```
"uid=1000" will mount the partition with you as owner
"umask=000" will make it r/w to everyone. This is the default but it's in the template so you can go back and change it if your requirements change.

---

### Post by Mesopotamia on 2013-05-06
Unfortunately, none of the methods mentioned above worked. It kept brining a message stating that the volume can not be mounted when I first boot Ubuntu.

I've provided the output of all the required commands.

```
____@Babylon:~$ sudo blkid -c /dev/null 
/dev/sda1: LABEL="Movies 02" UUID="3245783F4439C596" TYPE="ntfs" 
/dev/sdb1: LABEL="Mac Backup" UUID="25BC6E9613D3D5E7" TYPE="ntfs" 
/dev/sdb2: LABEL="Data" UUID="2ED051A8719ED0D0" TYPE="ntfs" 
/dev/sdb3: LABEL="Random Stuff" UUID="390BD77811097D56" TYPE="ntfs" 
/dev/sdc1: LABEL="Movies 03" UUID="42F34DD06CE57879" TYPE="ntfs" 
/dev/sdd1: LABEL="Movies 01" UUID="9C5ECFAF5ECF810E" TYPE="ntfs" 
/dev/sde1: LABEL="System Reserved" UUID="98886EF5886ED0F4" TYPE="ntfs" 
/dev/sde2: LABEL="Windows 7" UUID="DA847CD7847CB799" TYPE="ntfs" 
/dev/sde5: UUID="691e359a-810b-4bd5-9a7d-92c9618e062a" TYPE="swap" 
/dev/sde6: UUID="affeedcc-f9b3-46bf-9f54-d2001d37345d" TYPE="ext4" 
/dev/sdf1: UUID="EF33-5CBB" TYPE="vfat" 

```


Nothing in the fstab file except the RAMDisk.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid         0  0  

# / was on /dev/sda6 during installation
UUID=affeedcc-f9b3-46bf-9f54-d2001d37345d  /            ext4  errors=remount-ro           0  1  

# swap was on /dev/sda7 during installation
UUID=691e359a-810b-4bd5-9a7d-92c9618e062a  none         swap  sw                          0  0  



tmpfs                                      /mnt/RAMDisk tmpfs   defaults,       size=8192M        0  0


```
```
____@Babylon:~$ mount                                                                                                                                                                 
/dev/sde6 on / type ext4 (rw,errors=remount-ro)                                                                                                                                         
proc on /proc type proc (rw,noexec,nosuid,nodev)                                                                                                                                        
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)                                                                                                                                       
none on /sys/fs/cgroup type tmpfs (rw)                                                                                                                                                  
none on /sys/fs/fuse/connections type fusectl (rw)                                                                                                                                      
none on /sys/kernel/debug type debugfs (rw)                                                                                                                                             
none on /sys/kernel/security type securityfs (rw)                                                                                                                                       
udev on /dev type devtmpfs (rw,mode=0755)                                                                                                                                               
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)                                                                                                                       
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)                                                                                                                          
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)                                                                                                                      
none on /run/shm type tmpfs (rw,nosuid,nodev)                                                                                                                                           
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)                                                                                                          
tmpfs on /mnt/RAMDisk type tmpfs (rw)                                                                                                                                                   
gvfsd-fuse on /run/user/MyUsername/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=MyUsername)                                                                                                  
/dev/sdf1 on /media/MyUsername/EF33-5CBB type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)                                     
gvfsd-fuse on /home/MyUsername/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)                                                                                                                 
/dev/sdc1 on /media/MyUsername/Movies 03 type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks2)  

```

---

### Post by coffeecat on 2013-05-06
> **Mesopotamia said:**
> 
```
____@Babylon:~$ mount  

<snip>
                                                                                                                
/dev/sdc1 on /media/MyUsername/Movies 03 type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks2)  

```

That looks as though /dev/sdc1 has been mounted from the GUI, but is using the read-only ntfs kernel driver rather than the FUSE ntfs-3g driver. Did you uninstall the package ntfs-3g? Check your package manager. Re-install ntfs-3g if it isn't installed.

---

