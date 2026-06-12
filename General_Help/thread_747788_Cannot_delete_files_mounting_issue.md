---
title: "Cannot delete files/ mounting issue"
date: 2008-04-06
forum: General Help
---

### Post by Lolicon on 2008-04-06
I can move my files to the recycle bin fine, but I cannot delete them.
I tried:
> 
sudo konqueror

sudo rm -rf $HOME/.Trash/*


But they never delete.
I can write files fine on the partition but I can't delete them. 

The other partitions I have are never automounted, and I don't have write access to them.
Heres my fstab.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ee5702be-2183-4915-a4ee-87bf50107a10 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7188203e-e8a6-4083-aa94-7343bc3f72fe /media/sda1     ext2    defaults        0       2
# /dev/sda3
UUID=9EB83243B83219EB /media/sda3     ntfs    auto,user,umask=007,gid=46 0       1
# /dev/sda5
UUID=01C89732F97DF680 /media/sda5     ntfs    auto,umask=007,gid=46 0       1
# /dev/sdb1
UUID=6368746f-2074-616b-6f65-207575696400 /media/sdb1     ext3    auto        0       2
# /dev/sdb2
UUID=01C8123E28B0B200 /media/sdb2     ntfs    auto,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I'm on Hardy Heron if that helps.

---

### Post by Rocket2DMn on 2008-04-06
Can you also post
```
sudo fdisk -l
ls -l /dev/disk/by-uuid/
ls -l ~/.Trash/
```

---

### Post by Lolicon on 2008-04-06
> Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            7842       15067    58042812+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2               2        5166    41487862+   f  W95 Ext'd (LBA)
/dev/sda3   *       24639       28481    30868897+   7  HPFS/NTFS
/dev/sda4           30394       30394        8032+   e  W95 FAT16 (LBA)
/dev/sda5               2        3953    31744408+   7  HPFS/NTFS
/dev/sda6            3954        5166     9743391   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x125bc4f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       49719   399367836   83  Linux
/dev/sdb2           54819       60801    48058447+   7  HPFS/NTFS

Disk /dev/sdc: 16.2 GB, 16240344576 bytes
113 heads, 57 sectors/track, 4924 cylinders
Units = cylinders of 6441 * 512 = 3297792 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          13       40131    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13        4925    15819549    b  W95 FAT32
> lrwxrwxrwx 1 root root 10 2008-04-06 07:12 01C8123E28B0B200 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-04-06 07:12 01C89732F97DF680 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-04-06 07:12 3405-4C50 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-04-06 07:12 6368746f-2074-616b-6f65-207575696400 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-04-06 07:12 7188203e-e8a6-4083-aa94-7343bc3f72fe -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-06 12:12 7472-AF90 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2008-04-06 07:12 9EB83243B83219EB -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-04-06 07:12 ee5702be-2183-4915-a4ee-87bf50107a10 -> ../../sda6
I tnink I deleted the files, either there was a very slow refresh or something that was wrong got righted.
> ls: cannot access /home/w/.Trash/: No such file or directory
Thanks for the speedy response.

---

### Post by Rocket2DMn on 2008-04-06
OK, let's edit your fstab file
```
gksudo gedit /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ee5702be-2183-4915-a4ee-87bf50107a10 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7188203e-e8a6-4083-aa94-7343bc3f72fe /media/sda1     ext2    defaults        0       2
# /dev/sda3
UUID=9EB83243B83219EB /media/sda3     ntfs    defaults,locale=en_US.utf8 0       1
# /dev/sda5
UUID=01C89732F97DF680 /media/sda5     ntfs    defaults,locale=en_US.utf8 0       1
# /dev/sdb1
UUID=6368746f-2074-616b-6f65-207575696400 /media/sdb1     ext3    defaults        0       2
# /dev/sdb2
UUID=01C8123E28B0B200 /media/sdb2     ntfs    defaults,locale=en_US.utf8 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Save the file.
Then chown your ext2/3 partitions with
```
sudo chown -R yourusername:yourusername /media/[mountpoint]
```
That will make your username own everything on those partitions.  The other option is to change fstab options to set your username to have access.  You can read more here on that - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Then run
```
sudo mount -a
```
Post any errors you get.

---

### Post by Lolicon on 2008-04-06
No errors. Should I restart the system to check to see if it automounted?

---

### Post by Rocket2DMn on 2008-04-06
Sure.

---

### Post by Lolicon on 2008-04-07
didn't work. theres also an annoying check at the beginning of every bootup that says sda1 needs to be checked, then check forced.

---

### Post by Rocket2DMn on 2008-04-07
Your root partition entry in fstab is still a little weird, change it to
```
# /dev/sda6
UUID=ee5702be-2183-4915-a4ee-87bf50107a10 /               ext3    defaults,errors=remount-ro,noatime 0       1
```
You may need to run the disk check from the LiveCD, you can do that by booting to the LiveCD and running
```
fsck /dev/sda6
```
Your sda1 partition also shows
> Partition 1 does not end on cylinder boundary.
I'm not sure what's up with that.  When you made these partitions did it give you any errors?  Have you fiddled with the partitions at all?

For the automounting problem, are ANY of them automounting when you boot?  For those that don't run
```
sudo mount /dev/sd**
``` and post the errors here (where sd** is the correct partition).

---

### Post by unutbu on 2008-04-07
Your trash deletion problem reminded me of a directory with the 'append only' attribute set.

Would you please post

```
mount
ls -ld ~/.Trash
lsattr -d  ~/.Trash
```

---

### Post by Lolicon on 2008-04-08
> **Rocket2DMn said:**
> Your root partition entry in fstab is still a little weird, change it to
```
# /dev/sda6
UUID=ee5702be-2183-4915-a4ee-87bf50107a10 /               ext3    defaults,errors=remount-ro,noatime 0       1
```
You may need to run the disk check from the LiveCD, you can do that by booting to the LiveCD and running
```
fsck /dev/sda6
```
Your sda1 partition also shows

I'm not sure what's up with that.  When you made these partitions did it give you any errors?  Have you fiddled with the partitions at all?

For the automounting problem, are ANY of them automounting when you boot?  For those that don't run
```
sudo mount /dev/sd**
``` and post the errors here (where sd** is the correct partition).
Is it alright to do ```
sudo mount -a

``` instead? I'm thinking about just running a startup script every time I turn on my computer, is it possilbe to run some commands in terminal?
> **unutbu said:**
> Your trash deletion problem reminded me of a directory with the 'append only' attribute set.

Would you please post

```
mount
ls -ld ~/.Trash
lsattr -d  ~/.Trash
```
No such directory.

---

### Post by Rocket2DMn on 2008-04-08
> **Lolicon said:**
> Is it alright to do ```
sudo mount -a

``` instead? I'm thinking about just running a startup script every time I turn on my computer, is it possilbe to run some commands in terminal?

That will only mount the stuff in your fstab file, though it should give you errors, too.  fstab IS essentially your startup script, but it won't mount the filesystem if it has problems or if it  isn't declared correctly.  Using the mount command with only the device or destination will look to fstab for the entry.  You can override by using the full mount command
```
sudo mount -t [filesystemtype] /dev/[device] /media/[mountpoint]
```

---

### Post by Lolicon on 2008-04-08
> **Rocket2DMn said:**
> That will only mount the stuff in your fstab file, though it should give you errors, too.  fstab IS essentially your startup script, but it won't mount the filesystem if it has problems or if it  isn't declared correctly.  Using the mount command with only the device or destination will look to fstab for the entry.  You can override by using the full mount command
```
sudo mount -t [filesystemtype] /dev/[device] /media/[mountpoint]
```
Oddly enough it doesn't, and works all right as far as I can tell. Wow, there must be something screwy with my computer.

---

### Post by Rocket2DMn on 2008-04-08
So is everything mounting OK now?

---

### Post by Lolicon on 2008-04-08
If I put the command in there, its fine, thanks for teaching me it. Is there a way to run it as a startup script or something?

---

### Post by Rocket2DMn on 2008-04-09
You can run startup scripts, but it can be a bit of a pain to setup and should not be needed in this occassion (and may not even really be possible to run at login since mounting requires root priviliges, and running it directly at boot before login probably won't fix the problem).  So I'm going to ask you for a bunch of information now so I can find out exactly where we are (I got a little lost since this thread has taken a few days).  I also want to see changes you have made.
Please post
```
sudo fdisk -l
cat /etc/fstab
sudo mount -a
mount
```
Also, please tell me which partitions are still not mounting at boot.  Sorry if this is getting complicated/repetitive/frustrating.  Include any other information you might think is relevant, we are very close to getting this fixed.

---

### Post by Lolicon on 2008-04-11
> **Rocket2DMn said:**
> You can run startup scripts, but it can be a bit of a pain to setup and should not be needed in this occassion (and may not even really be possible to run at login since mounting requires root priviliges, and running it directly at boot before login probably won't fix the problem).  So I'm going to ask you for a bunch of information now so I can find out exactly where we are (I got a little lost since this thread has taken a few days).  I also want to see changes you have made.
Please post
```
sudo fdisk -l
cat /etc/fstab
sudo mount -a
mount
```
Also, please tell me which partitions are still not mounting at boot.  Sorry if this is getting complicated/repetitive/frustrating.  Include any other information you might think is relevant, we are very close to getting this fixed.

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            7842       15067    58042812+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2               2        5166    41487862+   f  W95 Ext'd (LBA)
/dev/sda3   *       24639       28481    30868897+   7  HPFS/NTFS
/dev/sda4           30394       30394        8032+   e  W95 FAT16 (LBA)
/dev/sda5               2        3953    31744408+   7  HPFS/NTFS
/dev/sda6            3954        5166     9743391   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x125bc4f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       49719   399367836   83  Linux
/dev/sdb2           54819       60801    48058447+   7  HPFS/NTFS

Disk /dev/sdc: 16.2 GB, 16240344576 bytes
113 heads, 57 sectors/track, 4924 cylinders
Units = cylinders of 6441 * 512 = 3297792 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          13       40131    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13        4925    15819549    b  W95 FAT32
```


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ee5702be-2183-4915-a4ee-87bf50107a10 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7188203e-e8a6-4083-aa94-7343bc3f72fe /media/sda1     ext2    defaults        0       2
# /dev/sda3
UUID=9EB83243B83219EB /media/sda3     ntfs    defaults,locale=en_US.utf8 0       1
# /dev/sda5
UUID=01C89732F97DF680 /media/sda5     ntfs    defaults,locale=en_US.utf8 0       1
# /dev/sdb1
UUID=6368746f-2074-616b-6f65-207575696400 /media/sdb1     ext3    defaults        0       2
# /dev/sdb2
UUID=01C8123E28B0B200 /media/sdb2     ntfs    defaults,locale=en_US.utf8 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

it gave me an error sometimes for some reason.
```
mount: /dev/sdb1 already mounted or /media/sdb1 busy
```

```
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-12-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/sda1 type ext2 (rw)
/dev/sda3 on /media/sda3 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb2 on /media/sdb2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/sdb1 type ext3 (rw)
```

---

### Post by Rocket2DMn on 2008-04-11
It looks like everything is mounted just fine.  I'm not sure why it gave that error for sdb1, maybe it was actually busy, but it says it is mounted at /media/sdb1.  Maybe it's because sdb1 has a boot flag.  In any case, it looks like you're good to go.

If the problem is solved, then sweet, you can mark the thread as [SOLVED] as shown in my signature.  Otherwise please be explicit about what is still wrong and we'll keep troubleshooting.

---

### Post by Lolicon on 2008-04-11
Basicly, no partitions besides the local partition mount at bootup. I guess I can live with sudo mount -a, but its a bit annoying to do it when Windows automaticly did it for me. I posted the mount after the manual mounting, so I don't think its solved yet. Should I post the mount when I haven't manually mounted it?

---

### Post by Rocket2DMn on 2008-04-11
Yes, might as well.  Make "mount" the first command you run after bootup.  We will try configuring fstab some more, probably just dumbing it down to the basics.

---

### Post by Lolicon on 2008-04-14
Heres a weird output of "sudo mount -a"
> Failed to mount '/dev/sda3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda3 /media/sda3 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda3 /media/sda3 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/sda5 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb2 /media/sdb2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb2 /media/sdb2 ntfs-3g force 0 0
w@Giga:~$ sudo mount -a force
mount: can't find force in /etc/fstab or /etc/mtab

Sorry I forgot to use mount on startup, but here it is after I tried the mount -a
> /dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-12-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/sda1 type ext2 (rw)
/dev/sdb1 on /media/sdb1 type ext3 (rw)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,noatime,uhelper=hal,flush,uid=1000,utf8,shortname=lower)


---

### Post by Lolicon on 2008-04-14
here is a clean startup mount:
> /dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-12-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


---

### Post by Rocket2DMn on 2008-04-14
OK, what it is saying is that the ntfs drives appear to be opened by windows, but not closed.  Do you have a dual boot?  Did you hibernate your windows partition?  If so, then that is why it won't mount them without forcing the mount.  Also, when you tried to force it to mount you forgot the -o.  The mount command looks like this:
```
sudo mount -t ntfs-3g /dev/sdb2 /media/sdb2 -o force
```
If you are dual booting and have windows hibernated or improperly shutdown, you should boot it up and shut it down normally.  Otherwise, use the force command.  After that it SHOULD mount normally.
If that doesn't work, I'm rapidly running out of ideas.

---

### Post by Lolicon on 2008-04-16
I edited the startup script and now it mounts everything automaticly. Thank you for your help rocket2dmn.

---

### Post by vanadium on 2008-04-17
Try to have the drive checked using Windows. It is a bad idea to continue to use force mount. At one moment, your partition might become heavily corrupt.

If you do not have windows and no possibility to check the drive on a Windows system, then you should copy your data from the drive and reformat the drive to a file system that Linux can fully repair. ext3 is an obvious choice, but for compatibility, fat32 would be the choice. Do not use a file system if you do not have the means of checking and repairing it.

---

### Post by Lolicon on 2008-04-19
> **vanadium said:**
> Try to have the drive checked using Windows. It is a bad idea to continue to use force mount. At one moment, your partition might become heavily corrupt.

If you do not have windows and no possibility to check the drive on a Windows system, then you should copy your data from the drive and reformat the drive to a file system that Linux can fully repair. ext3 is an obvious choice, but for compatibility, fat32 would be the choice. Do not use a file system if you do not have the means of checking and repairing it.

Oddly enough, the file system that has problems is an EXT3 formatted partition that ubuntu always tries to check up on startup. I always have to CTRL ALT DEL it to boot, but is there a way to fix the partition? I haven't had any problems with it.

---

