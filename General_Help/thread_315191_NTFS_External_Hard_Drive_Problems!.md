---
title: "NTFS External Hard Drive Problems!"
date: 2006-12-08
forum: General Help
---

### Post by nzk on 2006-12-08
I followed the NTFS-3G instructions at [http://ubuntuforums.org/showthread.php?t=217009/]("http://ubuntuforums.org/showthread.php?t=217009/")

But they have gotten me nowhere. I have an external hard drive that I need to be able to write to, problem is it's only NTFS. I cannot format it because it has important info. Does anyone have any ideas? Thanks.

---

### Post by taurus on 2006-12-08
Please post your /etc/fstab here!

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by houstonbofh on 2006-12-08
Also what kind of external hard drive? USB? Fireware? E-SATA? SCSI? NAS?

---

### Post by nzk on 2006-12-08
/etc/fstab returns:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=24211a22-07f4-475c-a941-81ef48832238 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=0081e46c-a40c-4d69-a217-d934993b5333 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


its a USB drive.

---

### Post by taurus on 2006-12-08
You don't have anything in /etc/fstab to mount your ntfs partitions at all!!!  In that case, what is the output of this command from a terminal then?

```
sudo fdisk -l
```

---

### Post by nzk on 2006-12-08
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

But what does that have to do with my External USB NTFS HDD?

---

### Post by taurus on 2006-12-08
I thought you want to mount your external drive, ntfs, in Ubuntu so you can use it!!!  Otherwise, I am not really sure what you are asking here...  And besides, you didn't even have your external drive plugged in!!!

---

### Post by nzk on 2006-12-08
Well, I just want to write files to it, thats all. It's plugged in, though.

---

### Post by taurus on 2006-12-08
Then how come the "sudo fdisk -l" didn't show it at all!!!

---

### Post by nzk on 2006-12-08
I did that command again:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes **Here it is!!! :)**
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

---

### Post by taurus on 2006-12-08
Okay, you need to edit your /etc/fstab to add an entry for it.  From a terminal, type

```
gksudo gedit /etc/fstab
```
Scroll down to the end and add this line to it.

```

/dev/sda1   /media/windows   ntfs-3g   defaults,locale=en_US.utf8    0     0

```
Save it and create a mount point and mount it...

```

sudo mkdir /media/windows
sudo mount -a
df -h
```

---

### Post by nzk on 2006-12-08
I did that, but it doesn't see my external HDD at all anymore.

---

### Post by taurus on 2006-12-08
What the output of this command then?

```
df -h
```

---

### Post by nzk on 2006-12-08
OK it shows up. However, clicking on it shows: "mount: only root can mount /dev/sda1 on /media/windows"

---

### Post by nzk on 2006-12-08
Filesystem            Size Used Avail Use% Mounted on
/dev/hda1              53G   38G   13G  75% /
varrun                252M  108K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
procbususb             10M  172K  9.9M   2% /proc/bus/usb
udev                   10M  172K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   8% /lib/modules/2.6.17-10-386/volatile

---

### Post by taurus on 2006-12-08
What does your /etc/fstab look like?

```
cat /etc/fstab
```

---

### Post by nzk on 2006-12-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=24211a22-07f4-475c-a941-81ef48832238 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=0081e46c-a40c-4d69-a217-d934993b5333 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1   /media/windows   ntfs-3g   defaults,locale=en_US.utf8    0     0

---

### Post by taurus on 2006-12-08
Does your external harddrive still show up with this command?

```
sudo fdisk -l
```
And you've also created a mount point for it, right!

```
sudo mkdir /media/windows
```

---

### Post by nzk on 2006-12-08
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris


amd yes, i did the mount point.

---

### Post by taurus on 2006-12-08
But you either didn't plug in your external harddrive your it is not power up because the system does not see it!!!  There's no output for your /dev/sda at all...

---

### Post by nzk on 2006-12-08
Oh wait nevermind:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

---

### Post by nzk on 2006-12-09
Soo... my computer sees my external HD. What now?

---

### Post by taurus on 2006-12-09
Now you can get stuff off it or write to it!!!

---

### Post by nzk on 2006-12-09
Trying to click on the External HD in nautilus returns a mount error: "mount: only root can mount /dev/sda1 on /media/windows"

---

### Post by taurus on 2006-12-09
Did you mount it first?  

```
df -h
```

---

### Post by nzk on 2006-12-09
Yeah. I thought it was a permissions problem since the computer is like "blah blah ROOT blah blah"

I did gksu nautilus but it didnt see the external hard drive. Any ideas?

---

### Post by taurus on 2006-12-09
```
df -h
```

---

### Post by nzk on 2006-12-09
Filesystem            Size Used Avail Use% Mounted on
/dev/hda1              53G   38G   13G  76% /
varrun                252M  108K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
procbususb             10M  172K  9.9M   2% /proc/bus/usb
udev                   10M  172K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   8% /lib/modules/2.6.17-10-386/volatile

---

### Post by taurus on 2006-12-09
You haven't mounted it so you can't access or use it!!!  You first need to mount it so make sure it is plugged in and the power is on.  Then, run this command to mount it...

```
sudo mount -a
df -h
```

---

### Post by nzk on 2006-12-09
```
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
```

---

### Post by taurus on 2006-12-09
Sounds there is something wrong with that /dev/sda1!!!  What is the output of this command and your /etc/fstab as well?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by nzk on 2006-12-09
sudo fdisk -l
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=24211a22-07f4-475c-a941-81ef48832238 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=0081e46c-a40c-4d69-a217-d934993b5333 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1   /media/windows   ntfs-3g   defaults,locale=en_US.utf8    0     0
```

By the way, thanks for all your help. I seriously appreciate it.

---

### Post by taurus on 2006-12-09
What happens when you run this command from a terminal?

```
sudo mount -t ntfs /dev/sda1 /media/windows
```
Looks to me like you only have Ubuntu on your machine, /dev/hda.  Is the external harddrive, /dev/sda1, an extra drive for storage or is something on it?

---

### Post by nzk on 2006-12-09
The external hard drive is for storage.

When I try to run that command it says:
```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by taurus on 2006-12-09
If that external drive is for storage, why not format it as ext3 filesystem since it's better to use ext3 to store files in Linux...

Wanna do that?

---

### Post by nzk on 2006-12-09
I would do that, but I need it to be readable by a Windows Machine. You see, after my CD burner broke, this is the only way to transfer large files. The external HDD is also easy, since I have files in the realm of 8gb.

---

### Post by taurus on 2006-12-09
Then why not make it a fat32/vfat filesystem...  And just so you know, Windows can read ext2/ext3 now with this program, [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by nzk on 2006-12-09
isnt fat32 limited to 4gb?

Also, is there a way to format it to a different type without erasing the files?

---

### Post by taurus on 2006-12-09
> **nzk said:**
> isnt fat32 limited to 4gb?

Probably.  Not sure since I don't use it and don't have anything that large but I doubt it!

> Also, is there a way to format it to a different type without erasing the files?
You will loose all your data when you convert to another filesystem.  However, I recommend you connect that external harddrive to a XP machine to chech the integrity of that filesystem since Ubuntu thinks there is something wrong with it...

And once everything is good, connect it back to Ubuntu machine and mount it again.

---

### Post by nzk on 2006-12-09
Argh. Fine, I'll format it to ext3. How do I do that?

---

### Post by nzk on 2006-12-09
Bump...

---

### Post by taurus on 2006-12-10
Warning.  The following command will _erase_ all data on your harddrive, /dev/sda1, so backup before you attend it!!!

Applications -> Accessories -> Terminal
```
sudo mke2fs -j /dev/sda1
```
Then, you need to edit your /etc/fstab and remove the old entry for /dev/sda1 and replace it with

```
/dev/sda1   /media/share   ext3   defaults   0   2
```
Now, create a new mount point and mount it.

```
sudo mkdir /media/share
sudo mount -a
df -h
```

---

### Post by nzk on 2006-12-10
Alright I formatted it. Now it is still complaining about mounting on windows, I mounted it through gparted, and that seemed to work. But I don't have read-write permissions. gksudo nautilus does nothing, any ideas?

---

### Post by nzk on 2006-12-10
I followed your instructions, I didn't see them last time (did everything with gparted). I'm going to sleep, I'm going to try to connect this to windows, but for now I have to figure out how to read/write. Thanks.

---

### Post by taurus on 2006-12-10
If you want to format it, you first need to unmount it...

```
sudo umount /dev/sda1
```
Then, format it with either gparted or the command that I included.  I am about to go to bed too...

---

### Post by nzk on 2006-12-10
Okay I formatted it into ext3. Problem is, I cant write anything to the drive. (Permissions problem) How do I fix that?!

Lastly, Windows does not see the drive :|

---

### Post by dmartinsca on 2006-12-10
nkz, i think that if you add a line to your fstab file for a device, then you need the 'user' option to be able to mount it through nautilus, however, it seems if you don't add a line to fstab then you can mount it through nautilus as long as you are a member of the plugdev group. So:
You can see if you are a member of the plugdev group by running 'groups' in a terminal. If plugdev is not listed, then run **sudo gpasswd -a <your user> plugdev**
Or, if you want to have a line in /etc/fstab to control mount options for the external drive, you'll need something like ```
/dev/sda1 /mnt/wherever ext3 defaults,user,other-options 0 0
```
I believe this was one of the reasons you couldn't mount the ntfs partition through nautilus. The other was that you needed to run a scandisk type program on the disk, either the windows chdsk or the linux ntfsfix (from the ntfsprogs package).

The permissions problem can probably be fixed by mounting the drive, then changing the permissions on the point it is mounted at.. **sudo chmod a+rwx /mnt/point**

For windows to recognize the drive, you need to install a driver for ext2/3 filesystems. You can get one from [www.fs-driver.org](www.fs-driver.org).

---

### Post by nzk on 2006-12-11
> **dmartinsca said:**
> nkz, i think that if you add a line to your fstab file for a device, then you need the 'user' option to be able to mount it through nautilus, however, it seems if you don't add a line to fstab then you can mount it through nautilus as long as you are a member of the plugdev group. So:
You can see if you are a member of the plugdev group by running 'groups' in a terminal. If plugdev is not listed, then run **sudo gpasswd -a <your user> plugdev**
Or, if you want to have a line in /etc/fstab to control mount options for the external drive, you'll need something like ```
/dev/sda1 /mnt/wherever ext3 defaults,user,other-options 0 0
```
I believe this was one of the reasons you couldn't mount the ntfs partition through nautilus. The other was that you needed to run a scandisk type program on the disk, either the windows chdsk or the linux ntfsfix (from the ntfsprogs package).

The permissions problem can probably be fixed by mounting the drive, then changing the permissions on the point it is mounted at.. **sudo chmod a+rwx /mnt/point**

For windows to recognize the drive, you need to install a driver for ext2/3 filesystems. You can get one from [www.fs-driver.org](www.fs-driver.org).

Is it okay if I literally put exactly that into the fstab? I mounted it with gparted, and did chmod, but it still...doesnt...let...me...write!!

---

### Post by nzk on 2006-12-13
bump

---

