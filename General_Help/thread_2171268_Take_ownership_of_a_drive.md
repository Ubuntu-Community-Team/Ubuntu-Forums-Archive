---
title: "Take ownership of a drive"
date: 2013-08-29
forum: General Help
---

### Post by TimEnid on 2013-08-29
Using Ubuntu 13.04

I have an internal hard drive that when i click permissions, it says ROOT. I am trying to change ownership so that they show up in Plex. i have tried "chown -R tim /media/tim/Media" (this is the name of the drive), and it just wont change. 
Also, i have another drive, and the permissions say "Owner: Me" "Group: Tim" access says none. I click the dropdown arrow to change where it says NONE, i can choose an option, but the second i click one, it goes right back to none. Any suggestions?

sudo blkid
```
/dev/sdb: LABEL="Miscellaneous" UUID="10a6fa16-fdbc-40cd-8759-d8d22094d250" TYPE="ext4" 
/dev/sda1: LABEL="Media" UUID="F2ACF216ACF1D557" TYPE="ntfs" 
/dev/sdc1: LABEL="500gb" UUID="0CBE3F0CBE3EEE38" TYPE="ntfs" 
/dev/sdd1: LABEL="Movies" UUID="86CEFEB2CEFE9A1F" TYPE="ntfs" 
/dev/sde1: UUID="caf7e20c-a0ed-46aa-a264-a7611c34a711" TYPE="ext4" 
/dev/sde5: UUID="b0eae91a-301f-4f28-b770-1dd2705f75df" TYPE="swap" 
/dev/sdf1: LABEL="Backup" UUID="c00e434f-d2fa-4f72-a74e-7bed424b3188" TYPE="ext4" 
/dev/sr1: LABEL="Utility_HD-CXU2" TYPE="iso9660" 
/dev/sdg1: LABEL="Buffalo 1.5tb" UUID="A8508E6E508E4354" TYPE="ntfs" 
/dev/sdm1: LABEL="Buffalo 3.0" UUID="7955F50022718F29" TYPE="ntfs" 
/dev/sr2: LABEL="HPLAUNCHER" TYPE="iso9660" 
/dev/sdn1: LABEL="HP SimpleSave" UUID="7C5632EA5632A534" TYPE="ntfs" 
/dev/sdo1: LABEL="NewVolume" UUID="0E48C80248C7E715" TYPE="ntfs" 

```

please let me know if you need further info.

---

### Post by squakie on 2013-08-29
I'm probably wrong, but here goes:

What you are seeing is not just a disk, it's the file system on that disk.  It is actually the file systems that get mounted.  As far as I know, ALL file systems are owned by root.  There is something you can do, but I don't know if it will help you or not:

[LIST]
[*]create a new folder, such as /home/mydisk
[*]sudo chmod xxx /home/mydisk, where "xxx" is one of the access settings such as 777 for everyone to have all access.
[*]sudo chown <a userid goes here - perhaps yours?> /home/mydisk
[*]now create an entry in fstab to mount your disk to that folder (mount point)
[/LIST]

For your second question, unless you are running as root you will not be able to change permissions on a file/folder with a different owner because you don't own it.  You must have super user priviledges to do so.  From the command line (terminal) you would use sudo chmod xxx <file or folder name>.  To do it from a GUI, you would use the command line and type sudo nautilus.  This will open the file manager but with super user priviledges.  At this point you could then click to see the permissions and then change them.  A VERY BIG CAUTION:  be EXTREMELY CAREFUL when using either method.  If you do so on any system file you could screw up you linux installation.

Somebody will correct me if I'm wrong, but that is what I've done in the past.

---

### Post by redmk2 on 2013-08-30
> **TimEnid said:**
> Using Ubuntu 13.04

I have an internal hard drive that when i click permissions, it says ROOT. I am trying to change ownership so that they show up in Plex. i have tried "chown -R tim /media/tim/Media" (this is the name of the drive), and it just wont change. 
Also, i have another drive, and the permissions say "Owner: Me" "Group: Tim" access says none. I click the dropdown arrow to change where it says NONE, i can choose an option, but the second i click one, it goes right back to none. Any suggestions?

sudo blkid
```
/dev/sdb: LABEL="Miscellaneous" UUID="10a6fa16-fdbc-40cd-8759-d8d22094d250" TYPE="ext4" 
[COLOR="#FF0000"]/dev/sda1: LABEL="Media" UUID="F2ACF216ACF1D557" TYPE="ntfs" 
/dev/sdc1: LABEL="500gb" UUID="0CBE3F0CBE3EEE38" TYPE="ntfs" 
/dev/sdd1: LABEL="Movies" UUID="86CEFEB2CEFE9A1F" TYPE="ntfs" [/COLOR]
/dev/sde1: UUID="caf7e20c-a0ed-46aa-a264-a7611c34a711" TYPE="ext4" 
/dev/sde5: UUID="b0eae91a-301f-4f28-b770-1dd2705f75df" TYPE="swap" 
/dev/sdf1: LABEL="Backup" UUID="c00e434f-d2fa-4f72-a74e-7bed424b3188" TYPE="ext4" 
[COLOR="#0000FF"]/dev/sr1: LABEL="Utility_HD-CXU2" TYPE="iso9660" [/COLOR]
[COLOR="#FF0000"]/dev/sdg1: LABEL="Buffalo 1.5tb" UUID="A8508E6E508E4354" TYPE="ntfs" 
/dev/sdm1: LABEL="Buffalo 3.0" UUID="7955F50022718F29" TYPE="ntfs" [/COLOR]
[COLOR="#0000FF"]/dev/sr2: LABEL="HPLAUNCHER" TYPE="iso9660" [/COLOR]
[COLOR="#FF0000"]/dev/sdn1: LABEL="HP SimpleSave" UUID="7C5632EA5632A534" TYPE="ntfs" 
/dev/sdo1: LABEL="NewVolume" UUID="0E48C80248C7E715" TYPE="ntfs" [/COLOR]

```

please let me know if you need further info.

If you can't change the ownership (or change permissions) of a partition, mostlikely it is due to that partition's not having a compatible file system (FS) type to the local OS.  File system types such as *TYPE="ntfs"* or *TYPE="vfat"* are not compatible.  These FS do not have a Linux configurable ownership or permissions table (chown, chmod).

The partitions in red (above) are what I am talking about.  The partitions in blue are CD/DVD and are read only and nothing can be changed on them.  The NTFS partitions have the ownership set at mount time via a driver (ntfs-3g).  This means if you want to mount them as owned by a specific user and group you can do that at mount time.  You can't change this once the partition is mounted as the *chown, chgrp and chmod *tools for ext partitions don't work with NTFS.

It would be a help to see the specific mounts you are using with */media/tim/Media" *and *the other drive *you have mentioned.  Post the output of these 3 terminal commands please```

getent passwd tim

mount

df -h

```
[QUOTE= squakie]
... the file systems that get mounted. As far as I know, ALL file systems are owned by root.
[/QUOTE]
By default *only root can mount a partition*.  This can be overridden when configuring a mount directive in /etc/fstab.

The root user does not own all file systems by default.  The Linux ownership scheme (ext for the present time) is set by the leftmost bit  in the scheme.  This is the extended bit  This bit is to the left of the commonly shown 3 bits (e.g. 755) for the default UID/GID it is set to 0 (e.g. 0755).  This scheme uses the logged in user as the owner of the file of folder at creation (UID)  and the users primary group to be the group owner (GID).  By default Debian and Ubuntu use user private groups (UPG).  
  
>  

There is something you can do, but I don't know if it will help you or not:

    create a new folder, such as /home/mydisk
    sudo chmod xxx /home/mydisk, where "xxx" is one of the access settings such as 777 for everyone to have all access.
    sudo chown <a userid goes here - perhaps yours?> /home/mydisk
    now create an entry in fstab to mount your disk to that folder (mount point)


This will not help the OP.  In fact, any directory in the system can have a subdirectory that is user readable and writable.   It does not have to be under /home. That is what /srv is for.  You could create a /srv/data  directory and chown and chmod that directory for the user to use.  Mounting a partition on that /srv/data directory in  no way affects or enhances a users ownership or permissions.  These are set at mount time.  When you mount ext partitions the ownership and permissions are auto-magically configured.  
> 

For your second question, unless you are running as root you will not be able to change permissions on a file/folder with a different owner because you don't own it. You must have super user priviledges to do so. From the command line (terminal) you would use sudo chmod xxx <file or folder name>. To do it from a GUI, you would use the command line and type sudo nautilus. This will open the file manager but with super user priviledges. At this point you could then click to see the permissions and then change them. A VERY BIG CAUTION: be EXTREMELY CAREFUL when using either method. If you do so on any system file you could screw up you linux installation.

Somebody will correct me if I'm wrong, but that is what I've done in the past. 

I'll bet you have only used ext formatted partitions to do this.  You will not be able to use chmod, chown or chgrp on NTFS and VFAT formatted partitions as I said before.  If you read some of the forum posts re: ownership and permissions of USB connected HDD's and USB connected flash drives,  you will see this topic covered time and time again.

Super user (root) or not, you can't change the owner or group for any directory or file on any mounted VFAT or NTFS partition.

---

### Post by nativehound on 2013-08-30
Couldn't he just edit the /etc/fstab and add the uid/gid? 
for example 
`UUID=[COLOR="#FF0000"]xxxxxxxxxxx[/COLOR]  [COLOR="#FF0000"]/media/tim/Media[/COLOR]  ntfs rw,auto,users,[COLOR="#FF0000"]uid=1000,gid=1000[/COLOR],permissions 0 2`
changing the red to the correct values.

---

### Post by squakie on 2013-08-30
I guess I should have been more specific:  of course you can't do this with NTFS; the /home/mydisk was only a sample, not a "rule";  I mount my NTFS partitions to a folder (where ever) and change the permissions on that folder to dictate access along with changes to fstab - that's why I mentioned doing what I did . Sorry I wasn't more specific. ;)

---

### Post by TimEnid on 2013-08-30
```
tim@tim:~$ getent passwd tim
tim:x:1000:1000:tim,,,:/home/tim:/bin/bash
tim@tim:~$ mount
/dev/sde1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdc1 on /media/tim/WD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/tim/Home type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
gvfsd-fuse on /run/user/tim/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=tim)
/dev/sr1 on /media/floppy0 type iso9660 (ro,nosuid,nodev,utf8)
/dev/sdm1 on /media/tim/Buffalo 3.02 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdg1 on /media/tim/Buffalo 1.5tb1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1 on /media/tim/Movies type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
tim@tim:~$ df  -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde1       106G   20G   81G  20% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            5.9G  4.0K  5.9G   1% /dev
tmpfs           1.2G  1.3M  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            5.9G  676K  5.9G   1% /run/shm
none            100M   20K  100M   1% /run/user
/dev/sdc1       466G  261G  206G  56% /media/tim/WD
/dev/sda1       466G  101G  366G  22% /media/tim/Home
/dev/sr1        198M  198M     0 100% /media/floppy0
/dev/sdm1       597G  121G  477G  21% /media/tim/Buffalo 3.02
/dev/sdg1       1.4T  303G  1.1T  22% /media/tim/Buffalo 1.5tb1
/dev/sdd1       932G  696G  237G  75% /media/tim/Movies
```

---

### Post by redmk2 on 2013-08-30
> **TimEnid said:**
> ```
tim@tim:~$ getent passwd tim
tim:x:1000:1000:tim,,,:/home/tim:/bin/bash
```

```

tim@tim:~$ mount
/dev/sde1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdc1 on /media/tim/WD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/tim/Home type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
gvfsd-fuse on /run/user/tim/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=tim)
/dev/sr1 on /media/floppy0 type iso9660 (ro,nosuid,nodev,utf8)
/dev/sdm1 on /media/tim/Buffalo 3.02 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdg1 on /media/tim/Buffalo 1.5tb1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1 on /media/tim/Movies type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

```

tim@tim:~$ df  -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde1       106G   20G   81G  20% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            5.9G  4.0K  5.9G   1% /dev
tmpfs           1.2G  1.3M  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            5.9G  676K  5.9G   1% /run/shm
none            100M   20K  100M   1% /run/user
/dev/sdc1       466G  261G  206G  56% /media/tim/WD
/dev/sda1       466G  101G  366G  22% /media/tim/Home
/dev/sr1        198M  198M     0 100% /media/floppy0
/dev/sdm1       597G  121G  477G  21% /media/tim/Buffalo 3.02
/dev/sdg1       1.4T  303G  1.1T  22% /media/tim/Buffalo 1.5tb1
/dev/sdd1       932G  696G  237G  75% /media/tim/Movies
```

Mounting in /media is usually reserved for media that can be unmounted and removed.  In this case most likely using a USB interface. I my guess is that the partitions (e.g. sda1, sdc1, sdm1, sdg1 and sdd1) are auto-mounted and auto detected.  Am I correct on this?  All the partitions we are talking about are mounted in /meda and they all used fuseblk.  The use of fuseblk indicates the auto detection of partition format and guessing NTFS, but not using ntfs-3g as the  driver.

All the mounted partitions have permissions and ownership is set as the default (e.g. (rw,nosuid,nodev,allow_other,**[COLOR="#FF0000"]default_permissions[/COLOR]**,blksize=4096).  Let's see what the default ownership and permissions really look like.  Post the output these commands.  Let's do that in separate ```
 blocks please.
[CODE]ls -ld /meda

ls -l /media/tim/WD

ls -l /meda/tim/Home

ls -l /media/tim/"Buffalo 3.02"

ls -l /media/tim/"Buffalo 1.5tb1"

ls -l /meda/tim/Movies
```

Note the " " surrounding the 2 Buffalo entries.

Do you want these partitions to have you as the owner and group ( i.e. tim:x:1000:1000)?

---

### Post by TimEnid on 2013-08-30
> **redmk2 said:**
> Mounting in /media is usually reserved for media that can be unmounted and removed.  In this case most likely using a USB interface. I my guess is that the partitions (e.g. sda1, sdc1, sdm1, sdg1 and sdd1) are auto-mounted and auto detected.  Am I correct on this? 

correct


> **redmk2 said:**
> Do you want these partitions to have you as the owner and group ( i.e. tim:x:1000:1000)?
Yes


ls -ld /media
```
drwxr-xr-x 7 root root 4096 Aug 23 17:54 /media

```

ls -l /media/tim/Movies
```
tim@tim:~$ ls -l /media/tim/Movies
total 3143604
-rw------- 1 tim tim 3218972709 Nov 15  2011 11-11-11 (2012).mkv
drwx------ 1 tim tim      20480 Aug 26 19:40 DVD Movies
drwx------ 1 tim tim      24576 May 25 20:06 Misc
drwx------ 1 tim tim      28672 Aug 29 19:07 plexmedialibrary
drwx------ 1 tim tim          0 May 14  2010 System Volume Information

```

[COLOR=#000000]ls -l /meda/tim/Home[/COLOR]
```
tim@tim:~$ ls -l /media/tim/Home
total 304
drwxrwxrwx 1 root root      0 Feb 19  2013 DCIM
drwxrwxrwx 1 root root   4096 May 25 20:51 Documents
drwxrwxrwx 1 root root 294912 Aug 27 19:29 Music
drwxrwxrwx 1 root root      0 Feb 18  2012 PDF
drwxrwxrwx 1 root root  12288 Jul 21 20:11 Pictures
drwxrwxrwx 1 root root      0 Oct  2  2011 $RECYCLE.BIN
drwxrwxrwx 1 root root      0 May 25 20:02 Videos

```
I provided the output for the drive i want to change.
Thanks

---

### Post by redmk2 on 2013-08-30
> **TimEnid said:**
> 
ls -ld /media
```
drwxr-xr-x 7 root root 4096 Aug 23 17:54 /media

```

ls -l /media/tim/Movies
```
tim@tim:~$ ls -l /media/tim/Movies
total 3143604
-rw------- 1 tim tim 3218972709 Nov 15  2011 11-11-11 (2012).mkv
drwx------ 1 tim tim      20480 Aug 26 19:40 DVD Movies
drwx------ 1 tim tim      24576 May 25 20:06 Misc
drwx------ 1 tim tim      28672 Aug 29 19:07 plexmedialibrary
drwx------ 1 tim tim          0 May 14  2010 System Volume Information

```

[COLOR=#000000]ls -l /meda/tim/Home[/COLOR]
```
tim@tim:~$ ls -l /media/tim/Home
total 304
drwxrwxrwx 1 root root      0 Feb 19  2013 DCIM
drwxrwxrwx 1 root root   4096 May 25 20:51 Documents
drwxrwxrwx 1 root root 294912 Aug 27 19:29 Music
drwxrwxrwx 1 root root      0 Feb 18  2012 PDF
drwxrwxrwx 1 root root  12288 Jul 21 20:11 Pictures
drwxrwxrwx 1 root root      0 Oct  2  2011 $RECYCLE.BIN
drwxrwxrwx 1 root root      0 May 25 20:02 Videos

```
I provided the output for the drive i want to change.
Thanks

You will need to edit the /etc/fstab file as the root user.  Let's start with the obvious one ( /media/tim/Home).  You can try this line at the bottom of the file```

UUID="0E48C80248C7E715" /media/tim/Home ntfs-3g rw,uid=1000,gid=1000,[COLOR="#0000FF"]fmask=002,dmask=002[/COLOR]	   0      0

``` ...This makes the user tim owner with rw permissions for the partition mounted at /media/time/Home.

[COLOR="#0000FF"]Edit: the dmask and fmask have been corrected to 002.  See above[/COLOR]

---

### Post by TimEnid on 2013-08-30
> **redmk2 said:**
> You will need to edit the /etc/fstab file as the root user.  Let's start with the obvious one ( /media/tim/Home).  You can try this line at the bottom of the file```

UUID="0E48C80248C7E715" /media/tim/Home ntfs-3g rw,uid=1000,gid=1000,fmask=664,dmask=775       0      0

``` ...This makes the user tim owner with rw permissions for the partition mounted at /media/time/Home.

did that. now fstab reads
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=caf7e20c-a0ed-46aa-a264-a7611c34a711 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=b0eae91a-301f-4f28-b770-1dd2705f75df none            swap    sw              0       0
/dev/sr1        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 /media/tim/WD ntfs defaults 0 0
/dev/sda1 /media/tim/Home ntfs defaults 0 0
UUID="0E48C80248C7E715" /media/tim/Home ntfs-3g rw,uid=1000,gid=1000,fmask=664,dmask=775	   0      0

```

also, after typing in sudo gedit /etc/fstab, i get
```
** (gedit:3551): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist


** (gedit:3551): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

```

I checked the drive after making that change, and its still the same. Owner: Root - with everything grayed out.

---

### Post by redmk2 on 2013-08-30
> **TimEnid said:**
> did that. now fstab reads
```
# /etc/fstab: static file system information.
#
[COLOR="#FF0000"]# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).[/COLOR]
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=caf7e20c-a0ed-46aa-a264-a7611c34a711 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=b0eae91a-301f-4f28-b770-1dd2705f75df none            swap    sw              0       0
/dev/sr1        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 /media/tim/WD ntfs defaults 0 0
/dev/sda1 /media/tim/Home ntfs defaults 0 0
UUID="0E48C80248C7E715" /media/tim/Home ntfs-3g rw,uid=1000,gid=1000,fmask=664,dmask=775	   0      0

```

also, after typing in sudo gedit /etc/fstab, i get
```
** (gedit:3551): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

** (gedit:3551): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

```

I checked the drive after making that change, and its still the same. Owner: Root - with everything grayed out.

I knew I should have asked you to show me the fstab file.  How can the partition be auto-detected if you have it listed in the fstab file already?  FWIW you should not use /dev/sdxx in fstab when declaring mount parameters.  See the header in the file for info ( in red above).```

/dev/sda1 /media/tim/Home ntfs defaults 0 0
```...You need to remove that line and reboot the system.

The errors are due to you opening a graphical application (gedit) in the terminal.  Also you should use gksudo when opening gedit.  Sudo is for terminal based apps and gksudo is for GUI based apps.

---

### Post by TimEnid on 2013-08-30
> **redmk2 said:**
> I knew I should have asked you to show me the fstab file.  How can the partition be auto-detected if you have it listed in the fstab file already?  FWIW you should not use /dev/sdxx in fstab when declaring mount parameters.  See the header in the file for info ( in red above).```

/dev/sda1 /media/tim/Home ntfs defaults 0 0
```...You need to remove that line and reboot the system.

The errors are due to you opening a graphical application (gedit) in the terminal.  Also you should use gksudo when opening gedit.  Sudo is for terminal based apps and gksudo is for GUI based apps.
ok, did that. And now its not grayed out anymore. It says:

Owner: Me
Access: Create and Delete Files
Group: Tim
Access: None
Others
Access: None

when i click where it says NONE, i am unable to change it.

---

### Post by redmk2 on 2013-08-30
> **TimEnid said:**
> ok, did that. And now its not grayed out anymore. It says:

Owner: Me
Access: Create and Delete Files
Group: Tim
Access: None
Others
Access: None

when i click where it says NONE, i am unable to change it.

I can't see your GUI interface.  How about you show me the permissions from the terminal or attach a screen shot of what you are talking about.  The owner should be the user: tim.  Do  you have a user named me?  What does access really mean?

Show me this```
ls -l /media/tim/Home
```

[COLOR="#0000FF"]Edit: You will never be able to change any ownership or permissions settings other than at mount time (fstab).  This is because the file system on the partition you are mounting at /media/tim/Home is formatted as NTFS.[/COLOR]

---

### Post by TimEnid on 2013-08-30
> **redmk2 said:**
> I can't see your GUI interface.  How about you show me the permissions from the terminal or attach a screen shot of what you are talking about.  The owner should be the user: tim.  Do  you have a user named me?  What does access really mean?

Show me this```
ls -l /media/tim/Home
```
No user named "Me". I have no idea why that command is showing the contents of a HD connected to my pc.
```
tim@tim:~$ ls -l /media/tim/Home
ls: cannot open directory /media/tim/Home: Permission denied
tim@tim:~$ sudo ls -l /media/tim/Home
[sudo] password for tim: 
total 120
d-------w- 1 tim tim 12288 Aug 25 13:47 Action - Blu ray
d-------w- 1 tim tim 16384 Oct  7  2012 Animation - Blu ray
d-------w- 1 tim tim  8192 Dec  1  2012 Comedy - Blu ray
d-------w- 1 tim tim 32768 Nov 21  2012 Drama - Blu ray
d-------w- 1 tim tim 12288 Sep  2  2012 Horror - Blu ray
d-------w- 1 tim tim  4096 Aug 30 21:14 Oblivion
d-------w- 1 tim tim     0 Jul  8  2011 $RECYCLE.BIN
d-------w- 1 tim tim 12288 Dec  1  2012 SciFi - Blu ray
d-------w- 1 tim tim 16384 Aug 30 21:13 Suspense - Blu ray
d-------w- 1 tim tim     0 Jul 14  2010 System Volume Information
d-------w- 1 tim tim  4096 Aug 24 18:19 We're The Millers 2013 WEBRiP XViD UNiQUE (SilverTorrent)
d-------w- 1 tim tim     0 Jun 24  2011 Western - Blu ray
d-------w- 1 tim tim  4096 Aug 29 20:54 Workout

```

[IMG]http://i39.tinypic.com/2cpw1ab.png[/IMG]

---

### Post by redmk2 on 2013-08-30
> **TimEnid said:**
> No user named "Me". I have no idea why that command is showing the contents of a HD connected to my pc.
```
tim@tim:~$ ls -l /media/tim/Home
ls: cannot open directory /media/tim/Home: Permission denied
tim@tim:~$ sudo ls -l /media/tim/Home
[sudo] password for tim: 
total 120
d-------w- 1 tim tim 12288 Aug 25 13:47 Action - Blu ray
d-------w- 1 tim tim 16384 Oct  7  2012 Animation - Blu ray
d-------w- 1 tim tim  8192 Dec  1  2012 Comedy - Blu ray
d-------w- 1 tim tim 32768 Nov 21  2012 Drama - Blu ray
d-------w- 1 tim tim 12288 Sep  2  2012 Horror - Blu ray
d-------w- 1 tim tim  4096 Aug 30 21:14 Oblivion
d-------w- 1 tim tim     0 Jul  8  2011 $RECYCLE.BIN
d-------w- 1 tim tim 12288 Dec  1  2012 SciFi - Blu ray
d-------w- 1 tim tim 16384 Aug 30 21:13 Suspense - Blu ray
d-------w- 1 tim tim     0 Jul 14  2010 System Volume Information
d-------w- 1 tim tim  4096 Aug 24 18:19 We're The Millers 2013 WEBRiP XViD UNiQUE (SilverTorrent)
d-------w- 1 tim tim     0 Jun 24  2011 Western - Blu ray
d-------w- 1 tim tim  4096 Aug 29 20:54 Workout

```


That looks ugly.  I want to see the fstab again.  Post the output of ```
cat /etc/fstab
```

What do you mean by this "*I have no idea why that command is showing the contents of a HD connected to my pc.*???

---

### Post by TimEnid on 2013-08-30
> **redmk2 said:**
> That looks ugly.  I want to see the fstab again.  Post the output of ```
cat /etc/fstab
```

What do you mean by this "*I have no idea why that command is showing the contents of a HD connected to my pc.*???
The command you told me to type, [COLOR=#000000][FONT=Ubuntu Mono]sudo ls -l /media/tim/Home, it showing the contents of my drive thats titled HP SimpleSave.

[/FONT][/COLOR]```
tim@tim:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=caf7e20c-a0ed-46aa-a264-a7611c34a711 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=b0eae91a-301f-4f28-b770-1dd2705f75df none            swap    sw              0       0
/dev/sr1        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 /media/tim/WD ntfs defaults 0 0
UUID="0E48C80248C7E715" /media/tim/Home ntfs-3g rw,uid=1000,gid=1000,fmask=664,dmask=775	   0      0

```

---

### Post by redmk2 on 2013-08-30
> **TimEnid said:**
> The command you told me to type, [COLOR=#000000][FONT=Ubuntu Mono]sudo ls -l /media/tim/Home, it showing the contents of my drive thats titled HP SimpleSave.

[/FONT][/COLOR]```
tim@tim:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=caf7e20c-a0ed-46aa-a264-a7611c34a711 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=b0eae91a-301f-4f28-b770-1dd2705f75df none            swap    sw              0       0
/dev/sr1        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 /media/tim/WD ntfs defaults 0 0
UUID="0E48C80248C7E715" /media/tim/Home ntfs-3g rw,uid=1000,gid=1000,fmask=664,dmask=775	   0      0

```

I think that is my mistake the UUID should be: F2ACF216ACF1D557.  Try that in fstab and the use this command to remount everything```
sudo mount -a
```

Tell me what you have listed then.

---

### Post by TimEnid on 2013-08-30
In case you need it
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x19ad14d7


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976769023   488383488    7  HPFS/NTFS/exFAT


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f891


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   976773119   488385536    7  HPFS/NTFS/exFAT


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8f3c04b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048  1953521663   976759808    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/sde: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051a0e


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   224921599   112459776   83  Linux
/dev/sde2       224923646   250068991    12572673    5  Extended
/dev/sde5       224923648   250068991    12572672   82  Linux swap / Solaris


WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdf: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  1465149167   732574583+  ee  GPT


Disk /dev/sdg: 1499.7 GB, 1499651727360 bytes
255 heads, 63 sectors/track, 182322 cylinders, total 2929007280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00078baf


   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63  2929002929  1464501433+   7  HPFS/NTFS/exFAT


Disk /dev/sdm: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eaa56


   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1              63  1250258624   625129281    7  HPFS/NTFS/exFAT


Disk /dev/sdn: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24aaf13f


   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1              63  3907024064  1953512001    7  HPFS/NTFS/exFAT


Disk /dev/sdo: 1499.6 GB, 1499598946304 bytes
255 heads, 63 sectors/track, 182315 cylinders, total 2928904192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00096e74


   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1            2048  2928904191  1464451072    7  HPFS/NTFS/exFAT

```
SDD1 and SDA1 are the drives i want to take ownership of. Both are formatted at NTFS. So i guess this is not possible, unless i format them to something else. Is that correct?

---

### Post by redmk2 on 2013-08-30
> **TimEnid said:**
> In case you need it
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x19ad14d7


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976769023   488383488    7  HPFS/NTFS/exFAT


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f891


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   976773119   488385536    7  HPFS/NTFS/exFAT


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8f3c04b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048  1953521663   976759808    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/sde: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051a0e


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   224921599   112459776   83  Linux
/dev/sde2       224923646   250068991    12572673    5  Extended
/dev/sde5       224923648   250068991    12572672   82  Linux swap / Solaris


WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdf: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  1465149167   732574583+  ee  GPT


Disk /dev/sdg: 1499.7 GB, 1499651727360 bytes
255 heads, 63 sectors/track, 182322 cylinders, total 2929007280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00078baf


   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63  2929002929  1464501433+   7  HPFS/NTFS/exFAT


Disk /dev/sdm: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eaa56


   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1              63  1250258624   625129281    7  HPFS/NTFS/exFAT


Disk /dev/sdn: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24aaf13f


   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1              63  3907024064  1953512001    7  HPFS/NTFS/exFAT


Disk /dev/sdo: 1499.6 GB, 1499598946304 bytes
255 heads, 63 sectors/track, 182315 cylinders, total 2928904192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00096e74


   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1            2048  2928904191  1464451072    7  HPFS/NTFS/exFAT

```
SDD1 and SDA1 are the drives i want to take ownership of. Both are formatted at NTFS. So i guess this is not possible, unless i format them to something else. Is that correct?

You can set the ownership at mount time only.  If you want to be able to change ownership then you  need to format the partitions as ext4 or some such file system that allows the -- user:group:others --  format.  NTFS and VFAT do not.

---

### Post by TimEnid on 2013-08-30
> **redmk2 said:**
> I think that is my mistake the UUID should be: F2ACF216ACF1D557.  Try that in fstab and the use this command to remount everything```
sudo mount -a
```

Tell me what you have listed then.
```
tim@tim:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=caf7e20c-a0ed-46aa-a264-a7611c34a711 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=b0eae91a-301f-4f28-b770-1dd2705f75df none            swap    sw              0       0
/dev/sr1        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 /media/tim/WD ntfs defaults 0 0
UUID="F2ACF216ACF1D557" /media/tim/Home ntfs-3g rw,uid=1000,gid=1000,fmask=664,dmask=775	   0      0

```

---

### Post by TimEnid on 2013-08-30
> **redmk2 said:**
> You can set the ownership at mount time only.  If you want to be able to change ownership then you  need to format the partitions as ext4 or some such file system that allows the -- user:group:others --  format.  NTFS and VFAT do not.

Then i guess i will work on formatting the drives. I really appreciate your help. I'm not an advanced user.

---

### Post by redmk2 on 2013-08-30
> **TimEnid said:**
> Then i guess i will work on formatting the drives. I really appreciate your help. I'm not an advanced user.

STOP!!!!

Do you really need to change the ownership?  What are the permissions after the last fstab change.  Show me again```
ls -l /media/tim/Home
```

---

### Post by TimEnid on 2013-08-30
> **redmk2 said:**
> STOP!!!!

Do you really need to change the ownership?  What are the permissions after the last fstab change.  Show me again```
ls -l /media/tim/Home
```
```
tim@tim:~$ sudo ls -l /media/tim/Home
[sudo] password for tim: 
total 304
d-------w- 1 tim tim      0 Feb 19  2013 DCIM
d-------w- 1 tim tim   4096 May 25 20:51 Documents
d-------w- 1 tim tim 294912 Aug 27 19:29 Music
d-------w- 1 tim tim      0 Feb 18  2012 PDF
d-------w- 1 tim tim  12288 Jul 21 20:11 Pictures
d-------w- 1 tim tim      0 Oct  2  2011 $RECYCLE.BIN
d-------w- 1 tim tim      0 May 25 20:02 Videos

```

---

### Post by TimEnid on 2013-08-30
Now, when i click on that drive, i get a message saying i do not have the permission necessary to view the contents of "HOME".

---

### Post by redmk2 on 2013-08-30
> **TimEnid said:**
> Now, when i click on that drive, i get a message saying i do not have the permission necessary to view the contents of "HOME".

It's easy to go back to the original.  You just add this line back in ```
/dev/sda1 /media/tim/Home ntfs defaults 0 0
```...and comment out the line we are having trouble with.  Like this```
**[COLOR="#FF0000"]##[/COLOR]** UUID="F2ACF216ACF1D557" /media/tim/Home ntfs-3g rw,uid=1000,gid=1000,fmask=664,dmask=775	   0      0
```

See the red hashes?

---

### Post by TimEnid on 2013-08-30
> **redmk2 said:**
> It's easy to go back to the original.  You just add this line back in ```
/dev/sda1 /media/tim/Home ntfs defaults 0 0
```...and comment out the line we are having trouble with.  Like this```
**[COLOR=#FF0000]##[/COLOR]** UUID="F2ACF216ACF1D557" /media/tim/Home ntfs-3g rw,uid=1000,gid=1000,fmask=664,dmask=775       0      0
```

See the red hashes?
That worked. thanks

---

### Post by nativehound on 2013-08-30
Change the permissions of dmask and fmask to fmask=137,dmask=027, `000` would give R-W-X
UUID=F2ACF216ACF1D557 /media/tim/Home ntfs-3g rw,auto,user,uid=1000,gid=1000,fmask=137,dmask=027       0      2

---

### Post by squakie on 2013-08-31
Humm, mounting to a specif mount point, using fstab to set permissions (which could have just been done on a different mount point).  Sounds suspiciously like what I stated to begin with......

---

### Post by redmk2 on 2013-08-31
> **squakie said:**
> Humm, mounting to a specif mount point, using fstab to set permissions (which could have just been done on a different mount point).  Sounds suspiciously like what I stated to begin with......

The mounting to a specific mount point using fstab is not in question.  The devil is in the details.   Your statement is incorrect when you state *"As far as I know, ALL file systems are owned by root."*.  That and lack of mentioning why the OP could not use chmod and chown on NTFS partitions were the 2 points I was making.  

You (as root) can make mount  points where ever you want in the file system.  You can provide any owner to the mount point as long as you also provide at least read and execute (r-X) to the users "others" on the mount point.  That way the all users will have access to that directory (mount point).  On the other hand, if you don't specify the owner (UID/GID) and the explicit umask (fmask and dmask) **when mounting an NTFS partition **you may not have ownership and permissions as you expect them to be and you can't change them on the fly with chmod and chown.

---

### Post by Morbius1 on 2013-08-31
I hope no one minds my usual interjection of comic relief but what further complicates this discussion is the unfortunate choice of /media/tim/moutpoint for the mountpoint location.

Look at the permissions of /media/tim ( remember this is Ubuntu 13.04 ) - and don't do it with a "ls -dl /media/tim" you will get the wrong answer, do it this way:
```
getfacl -t /media/tim
```
Only "tim" has access to that directory meaning only "tim" will have access to anything beyond it - doesn't matter what permissions are on the mount point itself.
[I]
[COLOR=#0000cd]Irrelevant side note at this point[/COLOR][/I]: this line in fstab did exactly what you told it to do:
> UUID="0E48C80248C7E715" /media/tim/Home ntfs-3g rw,uid=1000,gid=1000,fmask=664,dmask=775       0      0
umask, fmask, dmask represent [COLOR=#0000cd]permissions that you want removed[/COLOR] from the mounted partition - not the permissions you want it to have. A newborn ntfs partition has all permissions set to 777 for both files and folders so what you told it to do is mount with folder permissions of:

777 - 775 = 002

You will have a directory that has no permissions at all for user and group and this odd write permissions for others which is what you ended up with.

---

### Post by redmk2 on 2013-08-31
> **Morbius1 said:**
> I hope no one minds my usual interjection of comic relief but what further complicates this discussion is the unfortunate choice of /media/tim/moutpoint for the mountpoint location.

Look at the permissions of /media/tim ( remember this is Ubuntu 13.04 ) - and don't do it with a "ls -dl /media/tim" you will get the wrong answer, do it this way:
```
getfacl -t /media/tim
```
Only "tim" has access to that directory meaning only "tim" will have access to anything beyond it - doesn't matter what permissions are on the mount point itself.
[I]
[COLOR=#0000cd]Irrelevant side note at this point[/COLOR][/I]: this line in fstab did exactly what you told it to do:

umask, fmask, dmask represent [COLOR=#0000cd]permissions that you want removed[/COLOR] from the mounted partition - not the permissions you want it to have. A newborn ntfs partition has all permissions set to 777 for both files and folders so what you told it to do is mount with folder permissions of:

777 - 775 = 002

You will have a directory that has no permissions at all for user and group and this odd write permissions for others which is what you ended up with.
I saw the error with dmask and fmask and corrected it in my first directive.  The OP is aware via PM.

---

### Post by Morbius1 on 2013-08-31
> **redmk2 said:**
> I saw the error with dmask and fmask and corrected it in my first directive.  The OP is aware via PM.
I did not see that until this very minute - a thousand apologies.

---

### Post by squakie on 2013-08-31
> **redmk2 said:**
> ....You (as root) can make mount  points where ever you want in the file system.  You can provide any owner to the mount point as long as you also provide at least read and execute (r-X) to the users "others" on the mount point.  That way the all users will have access to that directory (mount point).  On the other hand, if you don't specify the owner (UID/GID) and the explicit umask (fmask and dmask) **when mounting an NTFS partition **you may not have ownership and permissions as you expect them to be and you can't change them on the fly with chmod and chown.

Just my opinion: between this and using /media for a mount point - which to me is not the wisest of ideas, you're over complicating a simple task, and not one most newbies will follow.  if you look at my post I mentioned using chmod and chown of the mount point, in what ever permissions you want.  Not on the fly - on a permanent mount point/folder.  Once done, it's done.  No need to complicate with the expanded fstab entry.  I do this with all of my NTFS external drives, and a NTFS partition on an internal drive should be no different, and it works fine, thank you.  I suggested a completely different mount point because then you can mount to a folder name that is more descriptive - the suggestion I gave was only an example.  

I also may have missed it, so I'm just putting this out there in case it's not there, but best to mount by uuid if a separate disk.  I do this with external USB drives so that another device doesn't come along - such as a USB flash, or a second (or whatever) internal drive installed - as this messes with the /dev/xxxx names.  Again, just didn't see if that was mentioned.

---

### Post by TimEnid on 2013-08-31
Thanks for the assistance everyone. So let me give you more details on what i want to do. There is a program called Plex. Its streams movies from your pc to multiple devices. I installed the app and have read that in order for Plex to se my movie drives, it needs certain permissions. I have been reading up on this for the past few days. I found these two threads and posted in them.
[http://ubuntuforums.org/showthread.php?t=2159071](http://ubuntuforums.org/showthread.php?t=2159071)
[http://ubuntuforums.org/showthread.php?t=2087341](http://ubuntuforums.org/showthread.php?t=2087341)

I tried to follow the directions in the threads, but have had no success. So, here is what i have in fstab, and here is a look at my drives.
```
[COLOR=#000000]*tim@tim:/media/tim$ ls -l*[/COLOR]
[COLOR=#000000]*total 484*[/COLOR]
[COLOR=#000000]*drwx------ 2 root root 4096 Aug 16 22:18 Buffalo 1.5tb*[/COLOR]
[COLOR=#000000]*drwx------ 1 tim tim 28672 Aug 31 01:33 Buffalo 1.5tb1*[/COLOR]
[COLOR=#000000]*drwx------ 2 root root 4096 May 6 16:52 Buffalo 3.0*[/COLOR]
[COLOR=#000000]*drwx------ 2 root root 4096 Aug 16 22:18 Buffalo 3.01*[/COLOR]
[COLOR=#000000]*drwx------ 1 tim tim 430080 Aug 31 11:00 Buffalo 3.02*[/COLOR]
[COLOR=#000000]*drwxrwxr-x 1 tim tim 8192 May 26 16:54 Home*[/COLOR]
[COLOR=#000000]*drwx------ 2 root root 4096 May 31 19:49 Iomega 3.0*[/COLOR]
[COLOR=#000000]*drwxrwxrwx 2 tim tim 4096 Apr 27 13:04 Media*[/COLOR]
[COLOR=#000000]*drwxrwxrwx 5 tim plugdev 4096 Aug 31 12:12 Movies*[/COLOR]
[COLOR=#000000]*drwxrwxrwx 1 root root 4096 May 25 19:55 WD*[/COLOR]
```
In the above, i only want the drives Movies and Home to be visible in Plex.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=caf7e20c-a0ed-46aa-a264-a7611c34a711 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=b0eae91a-301f-4f28-b770-1dd2705f75df none            swap    sw              0       0
/dev/sr1        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 /media/tim/WD ntfs defaults 0 0
## /dev/sda1 /media/tim/Home ntfs defaults 0 0
UUID="F2ACF216ACF1D557" /media/tim/Home ntfs rw,uid=1000,gid=1000,fmask=002,dmask=002       0      0

```

```
tim@tim:~$ sudo fdisk -l


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x19ad14d7


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976769023   488383488    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f891


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   976773119   488385536    7  HPFS/NTFS/exFAT


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8f3c04b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048  1953521663   976759808    7  HPFS/NTFS/exFAT


Disk /dev/sde: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051a0e


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   224921599   112459776   83  Linux
/dev/sde2       224923646   250068991    12572673    5  Extended
/dev/sde5       224923648   250068991    12572672   82  Linux swap / Solaris


WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdf: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  1465149167   732574583+  ee  GPT


Disk /dev/sdg: 1499.7 GB, 1499651727360 bytes
255 heads, 63 sectors/track, 182322 cylinders, total 2929007280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00078baf


   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63  2929002929  1464501433+   7  HPFS/NTFS/exFAT


Disk /dev/sdm: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eaa56


   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1              63  1250258624   625129281    7  HPFS/NTFS/exFAT


Disk /dev/sdn: 1499.6 GB, 1499598946304 bytes
255 heads, 63 sectors/track, 182315 cylinders, total 2928904192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00096e74


   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1            2048  2928904191  1464451072    7  HPFS/NTFS/exFAT

```

---

### Post by squakie on 2013-08-31
Again, you only need to do this once - it can't hurt to try, right?

- create a new folder wherever you want - I choose something in /home because then I don't have to worry about anyone having permissions into another folder I don't want:

sudo mkdir /home/mymedia

- now just change the permissions to what ever you want - if you don't mind anyone on your PC (usually I don't care since I'm the only one that uses it), you can just set to read/write for everyone:

sudo chown <your userid here> /home/mymedia

sudo chmod 777 /home/mymedia

the above would make you owner of the /home/mymedia folder, and give everyone read/write/execute priviledges to it - you can adjust this as you see fit

- be sure the ntfs-3g "things" are all installed

You now have a permanent mount point (the /home/mymedia folder) that you own and that everyone has full access to.  You only need to this once -that's it.  In the future, if you need to adjust ownership or permissions you can do so.

Now we need to know the unique univeral name for the partition or external device your media files are on:

sudo blkid

I tried to keep this sample simple, so I only have one NTFS partition mounted:

dave@dwezbox1:~$ sudo blkid
[sudo] password for dave: 
/dev/sda1: UUID="04fcfb33-42ed-40ab-8588-2d80e628700f" TYPE="ext4" 
/dev/sda5: UUID="b7f5fe57-8dcd-4da8-8926-b206707ec970" TYPE="swap" 
/dev/sr0: LABEL="SARARI_RIVER_SIMON_SECRET_JUNG^_" TYPE="udf" 
/dev/sdb1: LABEL="xbmc-shares" UUID="3B426B086C5EFD27" TYPE="ntfs" 
dave@dwezbox1:~$ 

As you can hopefully see, in this case /dev/sdb1 is an NTFS file system.  

Now, highlight, right click and click copy for the portion of that line starting at UUID= and to the end of the line.


- Now we need to tell the system that whenever that UUID is found we want to mount it to the permanent mount point we created - in this case /home/mymedia.  We do this by modifying the file system table, fstab:

sudo cp fstab fstab-save   (it's wise to create a backup of your original fstab, but don't overwrite it later!)

gksudo gedit fstab

- remove any of the entries you previously made to try to get this to work
- go to the end of the file
- right-click and click paste
this will copy in the uuid and file system type from what was copied from the blkid output

- now modify that line, adding what is new and removing the quotes. With my example it would be as follows, but you'll need to be sure to use your UUID and your mount point (/home/mymedia):

UUID=3B426B086C5EFD27   /home/shares TYPE=ntfs  defaults 0 0

Save the file and exit, then reboot.

You should now be able to:

ls -al /home/mymedia

and see your media files, their ownership and their permissions. What's at the folder level is what should matter:  /home/mymedia.  If the program you are using needs other access, it should be covered by the 777 permissions (everyone read/write/execute), but you can modify them as need via the command line "chmod".  Similarly, if the ownership needs to change, you can do that via the command line "chown".

Remember, you only need create the mount point (/home/mymedia) ONCE.  You need only set the permissions ONCE.  You (should) only need to change fstab ONCE.  From then on everything should work.  The beauty with this is that you are setting permissions and ownership from the command line, not in an fstab entry you may need to change (and reboot).  You can modify those permissions and ownership anytime you want.

I won't promise this will solve your problem - I need to go follow the links you posted to see what all they say. 

But, as I said - it can't hurt to try!

All we've done is create a permanent mount point ONCE, with permissions explicitly declared ONCE, mounted the file system to that mount point.

---

### Post by squakie on 2013-08-31
Also, be sure to follow this advice that was in one of the above threads,  The commands you would type in a terminal window are shown in the post:


[LIST]
[*]                                                                                                                                                                  January 16th, 2013                                                                                                                                                                                                     [#8]("http://ubuntuforums.org/showthread.php?t=2087341&p=12459273#post12459273")                                                                                                                                                                                              
                                                             [                                                      [IMG]http://ubuntuforums.org/customavatars/avatar337990_3.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=337990")                                                                                     [**[COLOR=#000000]jualin[/COLOR]**]("http://ubuntuforums.org/member.php?u=337990")      
                         [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]                                                                    Dark Roasted Ubuntu                                                                   [IMG]http://ubuntuforums.org/images/rank_9.png[/IMG]                                                                                                                                                                [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/im_aim.gif[/IMG]                            
                                      
             
                                                   Join DateJul 2007Beans1,062DistroUbuntu Development Release                                                           
                      
     
                                          **[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG] Re: Plex media Server cannot find media**[INDENT]                                   ...As others have mentioned  in other forums the problem is that the "plex" user doesn't belong to  the "plugdev" group which is the only group that has access to the  mounted devices. 



 All you need to do is to add plex to that group by using gpasswd 
     Code:
     sudo gpasswd -a plex plugdev 
To check that the "plex" user belongs to that group we can issue the following command:
     Code:
     groups plex 
Which should display something like: plex: plex plugdev

Restart your computer and try to access the mounted media with Plex  Media Manager. If for some reason that doesn't work then you might need  to add plex to your own user group. Some may consider this a bit risky  since plex would be able to do almost anything that your user (in my  case "jualin") can do.
Either way, we use gpasswd again:
     Paraphras: "The terminal command line is:"

     sudo gpasswd -a plex yourUS

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

From me:  it appears (I've never used it - I use xbmc) that when plex installs it create a user "plex". It also appears you need to add that user to the plugdev group as shown.  The command for doing this is shown, but I'll repeat it here:

sudo adduser plex plugdev


The permissions we gave the mount point (/home/mymedia) *should* work, but in case plex for some reason expects to own that mount point, just change the ownership with something like this:

sudo chown plex /home/mymedia

- text removed here -

As I mentioned, I use xbmc, and all of my ntfs partitions are mounted to various folders as I have described in my post prior to this, and I never have a problem with permissions.  

I'm also not sure if adding the user plex to the plugdev group is really needed in your case, since I believe that is only needed if you are using an external device such as a USB disk drive, but it won't hurt. 

Also, your output shows plugdev as the group the mount point belongs to.  If that is really needed (you'll just have to try and see what happens), just do the following:

sudo chgrp plugdev /home/mymedia


[/INDENT]
 
[/LIST]

---

### Post by Morbius1 on 2013-08-31
> **squakie said:**
> Just my opinion: between this and using /media for a mount point - which to me is not the wisest of ideas, you're over complicating a simple task, and not one most newbies will follow. [COLOR=#0000cd]** if you look at my post I mentioned using chmod and chown of the mount point, in what ever permissions you want.  Not on the fly - on a permanent mount point/folder.  Once done, it's done.  No need to complicate with the expanded fstab entry.**[/COLOR]  I do this with all of my NTFS external drives, and a NTFS partition on an internal drive should be no different, and it works fine, thank you.  I suggested a completely different mount point because then you can mount to a folder name that is more descriptive - the suggestion I gave was only an example.  

I also may have missed it, so I'm just putting this out there in case it's not there, but best to mount by uuid if a separate disk.  I do this with external USB drives so that another device doesn't come along - such as a USB flash, or a second (or whatever) internal drive installed - as this messes with the /dev/xxxx names.  Again, just didn't see if that was mentioned.

I stopped reading your post as soon as I saw the line highlighted above. Changing permissions of a mountpoint before the partition is mounted has no affect on the permissions of the partition after it's mounted. That's true if the partition being mounted is NTFS or EXT4. For EXT4 partitions you change the permissions after it's mounted but for NTFS you have to specify permissions in the fstab expression as it is mounted - even if all you do is specify the "defaults" option.. 

You don't have to take my word for it: Unmount the ntfs partition and change permissions of the mount point ot 700 then remount the partition with a "sudo mount -a". Since you specified only defaults in fstab it will mount with permissions of 777.

---

### Post by redmk2 on 2013-08-31
> **Morbius1 said:**
> I stopped reading your post as soon as I saw the line highlighted above. Changing permissions of a mountpoint before the partition is mounted has no affect on the permissions of the partition after it's mounted. That's true if the partition being mounted is NTFS or EXT4. For EXT4 partitions you change the permissions after it's mounted but for NTFS you have to specify permissions in the fstab expression as it is mounted - even if all you do is specify the "defaults" option.. 

You don't have to take my word for it: Unmount the ntfs partition and change permissions of the mount point ot 700 then remount the partition with a "sudo mount -a". Since you specified only defaults in fstab it will mount with permissions of 777.

+1  ;-)

---

### Post by squakie on 2013-08-31
So be it - all I know is that this all works for me.  If the partition is getting mounted with all permissions for everyone, it would still accomplish what I put in my post.  However, since everyone wants to shoot down everything I say here, even though THEIR solution didn't work, so be it.  You tell the user to add user plex to the plugdev group and see how it works - that is of course if you want to actually TRUST that something I posted IS correct.  If you don't, and plex isn't member of that group, and if permissions aren't set correctly (you did read the 2 links the OP posted, right), and you still get it to work - congradulations, you've discovered the key to a mystery for many people.  Hopefully you'll word it and provide answers in a way they can understand.

As fo me - I'm out of here (yeah I hear you saying "thank God").  Lotsa luck.

---

### Post by Morbius1 on 2013-09-01
Movies has read/write access to everyone and Home has at least read access by everyone. So far so good:
> drwxrwxrwx 5 tim plugdev 4096 Aug 31 12:12 Movies
drwxrwxr-x 1 tim tim 8192 May 26 16:54 Home
Me thinks it's not the partition or their permissions but where they are mounted that's the problem:
> /media/tim/Movies
/media/tim/Home
Would you mind posting the output of the following command:
```
getfacl -t /media/tim
```
We need to verify that the output looks something like this:
> getfacl: Removing leading '/' from absolute path names
# file: media/tim
USER   root      rwx     
user   tim     r-x     
GROUP  root      ---     
mask             r-x     
other            --- 
If it does look like the above then that's the problem. Access to an object in Linux is done through the path to that object and /media/tim is preventing everyone except root and "tim" from getting to whatever is beyond it. /media/tim is a system generated folder and is new since the LTS version of Ubuntu. If this were a Samba question there is a way around this problem but if this plex thing is a local process then I would suggest changing your mount point so that it's not under /media/tim:

***Unmount the Movies and Home partitions:***
```
sudo umount /media/tim/Movies
sudo umount /media/tim/Home
```
***Create new mountpoints one level up from where they are now:***
```
sudo mkdir /media/Movies
sudo mkdir /media/Home

```
***Change your fstab entries to reflect this new mount point then run the following command to mount these partitions to their new home:***
```
sudo mount -a
```

[COLOR=#0000cd]* If you have further difficulties of any sort please post the output of the following command so we can make specific recommendations to the fstab entries:*[/COLOR]
```
sudo blkid -c /dev/null
```

---

### Post by TimEnid on 2013-09-01
> **Morbius1 said:**
> Movies has read/write access to everyone and Home has at least read access by everyone. So far so good:

Me thinks it's not the partition or their permissions but where they are mounted that's the problem:

Would you mind posting the output of the following command:
```
getfacl -t /media/tim
```
We need to verify that the output looks something like this:

If it does look like the above then that's the problem. Access to an object in Linux is done through the path to that object and /media/tim is preventing everyone except root and "tim" from getting to whatever is beyond it. /media/tim is a system generated folder and is new since the LTS version of Ubuntu. If this were a Samba question there is a way around this problem but if this plex thing is a local process then I would suggest changing your mount point so that it's not under /media/tim:

***Unmount the Movies and Home partitions:***
```
sudo umount /media/tim/Movies
sudo umount /media/tim/Home
```
***Create new mountpoints one level up from where they are now:***
```
sudo mkdir /media/Movies
sudo mkdir /media/Home

```
***Change your fstab entries to reflect this new mount point then run the following command to mount these partitions to their new home:***
```
sudo mount -a
```

[COLOR=#0000cd]* If you have further difficulties of any sort please post the output of the following command so we can make specific recommendations to the fstab entries:*[/COLOR]
```
sudo blkid -c /dev/null
```

```
getfacl: Removing leading '/' from absolute path names
# file: media/tim
USER   root      rwx     
user   tim       r-x     
GROUP  root      ---     
mask             r-x     
other            --- 

```

Also, this may be a samba problem as well. I can no longer see my shared drives on my android devices.

```
tim@tim:~$ sudo blkid -c /dev/null/dev/sda1: LABEL="Media" UUID="F2ACF216ACF1D557" TYPE="ntfs" 
/dev/sdb: LABEL="Miscellaneous" UUID="10a6fa16-fdbc-40cd-8759-d8d22094d250" TYPE="ext4" 
/dev/sdd1: LABEL="Movies" UUID="fb47d03a-c5db-48ce-8712-adba506f2224" TYPE="ext4" 
/dev/sdc1: LABEL="500gb" UUID="0CBE3F0CBE3EEE38" TYPE="ntfs" 
/dev/sde1: UUID="caf7e20c-a0ed-46aa-a264-a7611c34a711" TYPE="ext4" 
/dev/sde5: UUID="b0eae91a-301f-4f28-b770-1dd2705f75df" TYPE="swap" 
/dev/sdf1: LABEL="Backup" UUID="c00e434f-d2fa-4f72-a74e-7bed424b3188" TYPE="ext4

```
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=caf7e20c-a0ed-46aa-a264-a7611c34a711 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=b0eae91a-301f-4f28-b770-1dd2705f75df none            swap    sw              0       0
/dev/sr1        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 /media/tim/WD ntfs defaults 0 0
## /dev/sda1 /media/Home ntfs defaults 0 0
   /dev/sdd1 /media/Movies ext4 defaults 0 0
UUID="F2ACF216ACF1D557" /media/tim/Home ntfs rw,uid=1000,gid=1000,fmask=002,dmask=002       0      0

```

edit: the movie drive has been found by Plex. I'm in business. However, i need to go into each folder and set the permissions for each file, since some of them are not showing up.

Thanks everyone for the help. I will make this as solved. If you see anything out of place in my fstab, please let me know.

Thanks

---

### Post by Morbius1 on 2013-09-01
After such a long fight to get to this point you're probably not in mood to change things but sometime in the future you might want to change this:
```
/dev/sdd1 /media/Movies ext4 defaults 0 0
```
To this:
```
UUID=fb47d03a-c5db-48ce-8712-adba506f2224  /media/Movies ext4 defaults 0 0
```
Linux gets confused every now and then when using /dev/sdxy method of identifying partitions - what may be sdd1 now may be sdc1 tomorrow. The problem gets worse the more of them you have and let's face it you have a lot of partitions. UUID's pretty much guarantees that that partition is the correct one.

Don't forget you need to fix this one as well:
> UUID="F2ACF216ACF1D557" [COLOR=#0000cd]/media/Home[/COLOR] ntfs rw,uid=1000,gid=1000,fmask=002,dmask=002       0      0
If you have created samba shares of these two you need to go back and make sure you change the path to point to the right folder now that the mount points have changed.

---

### Post by TimEnid on 2013-09-01
> **Morbius1 said:**
> After such a long fight to get to this point you're probably not in mood to change things but sometime in the future you might want to change this:
```
/dev/sdd1 /media/Movies ext4 defaults 0 0
```
To this:
```
UUID=fb47d03a-c5db-48ce-8712-adba506f2224  /media/Movies ext4 defaults 0 0
```
Linux gets confused every now and then when using /dev/sdxy method of identifying partitions - what may be sdd1 now may be sdc1 tomorrow. The problem gets worse the more of them you have and let's face it you have a lot of partitions. UUID's pretty much guarantees that that partition is the correct one.

Don't forget you need to fix this one as well:

If you have created samba shares of these two you need to go back and make sure you change the path to point to the right folder now that the mount points have changed.
Thanks. I have made these changes. Your help was greatly appreciated.

---

### Post by squakie on 2013-09-07
My personal apoligies to everyone here - I've been doing some investigating this week when I've had time and can report the following:

The only reason mine were working was because I wanted 777 permissions, so that's what I had set so obviously I didn't see a difference after the mount.  I've been working on 2 new media servers and wanted to restrict access on them and that's when I noticed I was getting more permissions than I wanted on those - as you showed in this thread.  I followed your advice here and have those working as needed.  Thank you.

I know I answered at least one other thread incorrectly about these permissions as well somewhere in the past - if they wanted all acces then it just luckily worked but not for the right reasons.  I know where it gets moutned, etc., makes no difference - hence my mount points are completely different from this post.  My external drives containing the media files are always in NTFS, and my mount statements themselves were working - "just" the permissions showed as I wanted but not thanks to my doing.

Again, I apologize.  I was only adamant about this because for my needs at the time it was working - but now I now only by "accident" and not by what I did.

---

### Post by AFriendlyNerd on 2013-10-19
Thank you Morbius! The /media/username/folder was the issue for me, and moving it to /media/ solved it! At some point it got put there by default. I wish I was smart enough to remember why, so that more people might be helped.

---

