---
title: "Mounting a 3rd drive in Server 14.04"
date: 2015-10-01
forum: General Help
---

### Post by zoidberg2 on 2015-10-01
I’ve added a third hard drive to my Ubuntu 14.04 server to backup data from my additional drive like music, films,  ISO files etc but I’m unable to mount this new 3[SUP]rd[/SUP] drive.

The first thing I did was create a directory in the /mnt folder called backup
```
cd /mnt

mkdir backup
```

The new drive is formatted with NTFS because I have a few Windows clients on the network. 
```
I run sudo blkid & get this output 

/dev/sdb1: LABEL="MediaBackup" UUID="96FA3FDDFA3FB7F7" TYPE="ntfs"
```

So I then go to /etc/fstab 

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f55c8fa7-9654-45a6-a7cb-200b04f977f9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2878ece3-7534-4786-ae6a-968ab0723fbf none            swap    sw              0       0

##Media Drive

UUID=6ACA1FCBCA1F9285 /mnt/media ntfs defaults 0 2

```

I added this line & rebooted the server 

```
UUID=96FA3FDDFA3FB7F7 /mnt/backup ntfs defaults 0 2
```

During the reboot the server hangs & tells that it can't mount the drive & gives me an option to proceed without mounting or go in to the terminal to fix it. 

Any ideas what the problem is? I ran a diskcheck on the hard drive & it found no errors.

---

### Post by btindie on 2015-10-01
Why did you reboot? You could have just mounted it with
```
sudo mount /mnt/media
```
which would then give any errors on the terminal.

I don't use NTFS myself but I think you need to use ntfs-3g for the type if you want read/write access.

Make sure you can mount it manually from the terminal before editing /etc/fstab. e.g.
```
sudo mount -t ntfs-3g /dev/sdb1 /mnt/backup
-or-
sudo mount -t ntfs-3g -U 96FA3FDDFA3FB7F7 /mnt/backup
```

---

### Post by oldfred on 2015-10-01
You created /mnt/backup, but tried mounting to /mnt/media?

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

   For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

You need to have a Windows repair flash drive, as NTFS will need chkdsk. But Linux cannot run that.

---

### Post by zoidberg2 on 2015-10-01
I followed the steps above & when I tried to mount it using mount /mnt/backup I got this message, 

```
root@server:~# sudo mount /mnt/backupThe disk contains an unclean file system (0, 1).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```

I'm assuming that this is because fast start up is enabled on Windows where I formatted the drive? So would I have to plug it back in to the Windows desktop, disable quick start up & then remove the drive? 

Does it have to be the same Windows computer I used to create the partition or could I use any Windows computer?

---

### Post by oldfred on 2015-10-01
Windows 8 or later with its fast startup or always on hibernation leaves all NTFS partitions with the hibernation flag set. And then Linux NTFS drive will not open it.

If you have no data in partition, you can try this:
 Force removal of hiberfil from Ubuntu
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

Or just see if you can totally reformat drive. You might have to use dd to zero out MBR if MBR(msdos) partitioned. If gpt then you may be able to use gdisk.

---

