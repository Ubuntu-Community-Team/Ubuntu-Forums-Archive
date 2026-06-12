---
title: "Failed Command Line Mount = Problem for PCManFM"
date: 2013-02-06
forum: General Help
---

### Post by Maneer on 2013-02-06
I am prettu sold on Lubuntu these days and have managed mostly to purge Microsoft from my life and I am encouraging others to do the same. I have one issue...
 
I have a Fat32 volume on my HD, which I use for saving all of my documents, so that they will be available to any OS. I know that theoretically, in Lubuntu, I should be able to set this filesystem to auto-mount at startup using Prefrences --> Disks but this has always generated an error so I gave up on that and wrote a shell script to mount the filesystem and open the directory in the Lubuntu file manager: PCManFM...
 
#!/bin/bash
sudo mount /dev/sda5 ../../media/user/USER\ FILES
pcmanfm ../../media/user/USER\ FILES/docs
exit #
 
I have successfully added the following to the bottom of the sudoers file using: sudo visudo, so that this script can run without being prompted for the password...
 
%user lenovo-3000-n100=(ALLNOPASSWD:/bin/mount
%user lenovo-3000-n100=(ALLNOPASSWD:/bin/umount
 
This seems to work and I have succesfully created a desktop sortcut to run the shell script...
 
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Documents
Name[en_GB]=Documents
Exec=/home/user/bin/documents.sh
Comment[en_GB]=
Terminal=false
 
All works fine unless you (accidentally) unmount the filesystem in PCManFM. The file manger can - seemingly - successfully unmount the filesystem, although SOMETIMES it asks for password authentication, despite umount being allowed in the sudoers file. Interestingly, in a terminal, attempting umount USER\ FILES or umount 0B4F-16DE always produces the following error: ...is not mounted (according to mtab).
This, despite the fact that the directory /mnt/0B4F-16DE exists. The bigger problem comes when you try to re-mount the same filesystem by double clicking it in PCManFM, rather than by running the shell script again. This always produces the following error, whilst running the shell script again works fine:
 
Error ounting system-managed device /dev/sda5: Command line mount
/mnt/0B4F-16DE exited with non-zero exit status 32: mount: wrong fs
type, bad option, bad superblock on /dev/sda5
Missing codepage or helper program, or other error. In some cases
useful info is found in syslog - try dmesg | tail or so
 
Trying dmesg | tail gives the output:
[ 337.620626] FAT-fs (sda5: Unrecognised mount option "x-gvfs-show"
or missing value
 
I guess that these errors are to a trained eye, indicating pretty precisely what is wrong with my shell script but I am at a loss as to how to interpret this. I have tried a couple of other variants of the shell script, yet it appears that the previous attempts have left some unfinished busniess which I should like to ask my computer to forget about, so that I can begin afresh.
 
I know that somthing is wrong because although, when the filesystem is mounted, I can open files and browse directories in PCManFM and even right click to Create New Blank File, I cannot save to this location, delete anything or copy files from any other volume to this location, because these attempts result in a permissions error. I have no such problems with other FAT32 filesystems, such as my USB drive. Any pointers appreciated.

---

### Post by aolong62 on 2013-02-06
Would it not make sense to mount the file system via fstab.

---

### Post by Morbius1 on 2013-02-06
You went through a lot of contortions to overcome the idiocy of the "Disks" utility which should never have been shipped.

Please post the output of each of the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by Maneer on 2013-02-06
Here is the output from the commands you asked me to run:

sudo blkid -c /dev/null

/dev/sda1: LABEL="WINDOWS XP" UUID="3418-3B85" TYPE="vfat" 
/dev/sda3: LABEL="SERVICEV001" UUID="24F1-D005" TYPE="vfat" 
/dev/sda5: LABEL="USER FILES" UUID="0B4F-16DE" TYPE="vfat" 
/dev/sda6: LABEL="LINUX BOOT" UUID="a788982d-97eb-4566-94bc-e8e24d8417ef" TYPE="ext4" 
/dev/sda7: UUID="2d28cf6b-f78b-408b-8966-4fe340e70ce3" TYPE="swap"

----------

mount

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/user/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=user)
/dev/sda1 on /media/user/WINDOWS XP type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

After mounting the filesystem with my script the following line is added in the output of mount:

/dev/sda5 on /media/user/USER FILES type vfat (rw)

After mounting the filesystem in PCManFM the following is shown, different from mounting with my script:

/dev/sda5 on /media/user/USER FILES type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

----------

cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=a788982d-97eb-4566-94bc-e8e24d8417ef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2d28cf6b-f78b-408b-8966-4fe340e70ce3 none            swap    sw              0       0
/dev/disk/by-label/SMART\134x20BTMGR /mnt/SMART\134x20BTMGR auto nosuid,nodev,nofail,noauto 0 0
/dev/disk/by-label/USER\134x20FILES /mnt/USER\134x20FILES auto nosuid,nodev,nofail,x-gvfs-show,noauto 0 0
/dev/disk/by-label/WINDOWS\134x20XP /media/user/WINDOWS\134x20XP auto nosuid,nodev,nofail,x-gvfs-show,noauto 0 0

If I remove these last two entries from fstab and reboot, I can resolve most of my problems, I can then mount and unmount USER FILES  either with my script or with PCManFM. However I still have some permissions issues meaning that after the filesystem is un-mounted and re-mounted it is subsequently writable by root but not by user.

I think that the first suggestion - in answer to my original query - was probably a good one, to forget the mount script and instead mount the filesystem in fstab but the Disks utility - which presumably edits fstab - seemingly cannot get the syntax right in order to successfully do that.

---

### Post by Morbius1 on 2013-02-06
Whew! This is what I would do:

*** These 2 at least have to go:
> /dev/disk/by-label/USER\134x20FILES /mnt/USER\134x20FILES auto nosuid,nodev,nofail,x-gvfs-show,noauto 0 0
/dev/disk/by-label/WINDOWS\134x20XP /media/user/WINDOWS\134x20XP auto nosuid,nodev,nofail,x-gvfs-show,noauto 0 0*** Create mountpoints away from /media/user:
```
sudo mkdir /mnt/UserFiles
sudo mkdir /mnt/WinXP
```*** Add the following to the end of fstab:
```
UUID=0B4F-16DE /mnt/UserFiles vfat defaults,utf8,uid=1000,umask=000 0 2
UUID=3418-3B85 /mnt/WinXP vfat defaults,utf8,uid=1000,umask=000 0 2
```*** If you have any of these partitions currently mounted unmount them.

*** Then run the following command which will test for errors and if there are none mount the partitions without a reboot:
```
sudo mount -a
```Then check to see if everything is working as you want. 

I'm not sure and there certainly is no way of knowing from the mess Disks made what kind of permissions you want on those partitions but we can modify the umask values if needed. Right now it's set to have you as owner and allows access to all local users.

---

### Post by Maneer on 2013-02-07
Thanks Morbius, your method worked like a dream, including write privileges. I needed to add the following to the appropriate line in /etc/fstab for any filesystem which I would like to see in PCManFM.

x-gvfs-show

The line is now:

/dev/sda5 /mnt/user_files vfat defaults,utf8,uid=1000,umask=000,x-gvfs-show 0 2

I think that this whole fiasco has been caused by an issue with PCManFM. If you use the eject button in the PCManFM GUI to un-mount a filesystem you will subsequently receive the error detailed in my original question: mount wrong fs type...

You will receive this error whether you try to re-mount the filesystem by double clicking its icon in PCManFM or by issuing:

sudo mount -a

In order to clear the error I was forced to edit the line in /etc/fstab as follows, removing x-gvfs-show

/dev/sda5 /mnt/user_files vfat defaults,utf8,uid=1000,umask=000 0 2

then issue:

sudo mount -a

then restore the line in /etc/fstab once again to:

/dev/sda5 /mnt/user_files vfat defaults,utf8,uid=1000,umask=000,x-gvfs-show 0 2

then again issue:

sudo mount -a

So, whilst this is useful fix to know, better still not to eject fixed disks using PCManFM's eject button. 

----------

NB: Double-clicking a filesystem in PCManFM mounts the filesystem at /media/user so be sure to un-mount any filesystem before specifying a different mount point in /etc/fstab

NB: When editing /etc/fstab I chose to refer to my filesystem as /dev/sda5 rather than as UUID=0B4F-16DE this is just my preference for ease of typing, I know of no practical difference in operation.

---

### Post by Morbius1 on 2013-02-08
I think I'm beginning to understand the nature of the problem .... maybe.

"x-gvfs-show" is a new option ( udisks2 ) that forces the device to show up in the UI where <fill in the name of your personal deity> never intended. 

The problem is that it shows it as a device that a user can unmount and mount which of course he cannot because he is not root. [COLOR=Blue]*As a side issue of course if why a user wants to or be permitted to unmount an auto-mounted partition. If a user want's that ability don't have the partition auto-mount.*[/COLOR]

Anyway, an alternative to this is to remove "x-gvfs-show" from fstab, open pcmanfm, go to /mnt/user_files, and bookmark it. It will show up on the left side panel of pcmanfm as just another folder. 
> NB: When editing /etc/fstab I chose to refer to my filesystem as  /dev/sda5 rather than as UUID=0B4F-16DE this is just my preference for  ease of typing, I know of no practical difference in operation.     That's fine and it will continue to work for as long as it will work and then it won't. Back in the olden tymes /dev/sdxy was the standard way to do this sort of thing and then problems started to arise where especially on multi-disk systems sdb1 became sda1 on boot and messed everything up. So then it was decided that using UUID or LABEL was the best approach. Things have gotten so complicated that now the thinking is that /dev/disk/by-uuid/uuid# is the best way to go since it fixes some problems like double mount icons and such.

They are over thinking the plumbing I'm afraid so things are beginning to plug up.

---

### Post by Maneer on 2013-02-12
Dear Morbius,
You have indeed understood my problem very well. I came to the same realisation through trial and error. I noticed after a couple of re-boots that x-gvfs-show can under certain circumstances (I cannot be entirely sure which circumstances) cause automout of the filesystem to fail at startup. Meaning that startup will pause and give the user the option to skip or enter manual recovery.

I stumbled upon the idea of removing x-gvfs-show and simply bookmarking the filesystem by draging to PCManFM's sidebar the folder icon of the directory whereto the filesystem is mounted... Exactly as you suggest.

I think that whoever is working on the Disks utility for the next release should know about this because as it stands, x-gvfs-show is what Disks adds to /fstab so I can only assume that there are others out there tearing their hair out over similar problems.

Thanks for the warning about use of /sda designations in /fstab I shall bear that in mind in future. For now, at least my problems are over.

---

