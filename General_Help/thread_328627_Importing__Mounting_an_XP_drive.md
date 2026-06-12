---
title: "Importing / Mounting an XP drive"
date: 2006-12-31
forum: General Help
---

### Post by Anakist on 2006-12-31
I have just installed Edgy and I am trying to bring in all the HDDs on this machine. I removed all the HDD except the one I was installing onto when I installed, now I want all my media files available.

I don't have the System/Admin/Disks application on here apparently, is there some way I can get it available and then play my music?

James

---

### Post by logos34 on 2006-12-31
Open a terminal and type:

$ sudo fdisk -l
$ cat /etc/fstab
$ cat /etc/mtab

Post the output.

---

### Post by Anakist on 2006-12-31
sudo fdisk -l:

Disk /dev/hda: 20.0 GB, 20020396032 bytes
16 heads, 63 sectors/track, 38792 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18465     9306328+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           18472       37772     9727357+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3           37786       38790      506520    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdd: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        2498    20065153+   7  HPFS/NTFS

$ cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8b5556b3-30c5-4ba1-9ef8-ed4de9ae0360 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6E703EB5703E83BD /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=84e107b8-0613-4ecb-9808-856103240edc none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

cat /etc/mtab:

/dev/hda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
/dev/hda1 /media/hda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hdb /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=james 0 0

EDIT: I should point out that I want to mount the 200gb drive because that has my download folder, videos and music on it.

James

---

### Post by Anakist on 2007-01-01
In GParted I get the following:

"Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.

Did you install the correct plugin for this filesystem?"

That is for all the NTFS HDDs in the computer except the OS install HDD which is a 20gig partitioned basically in half, NTFS on one half, ext3fs one half, and about 500mb for swap file.

James

---

### Post by logos34 on 2007-01-01
> "Unable to read the contents of this filesystem!

Gparted is checking your filesytem consistency and could be finding cluster accounting mismatches.

Or an antivirus program could be causing a problem. 

Defrag your windows volumes hdc and hdd if you haven't already.  Then run Check Disk/error checking with repair option and reboot TWICE.  

If successful, then you can move on to creating mount points and editing your fstab file.

*If you want to find out the exact cause of the error messages, boot from the Gparted livecd; when you get to the main window open a terminal and enter

> ntfsresize --info --force --no-progress-bar /dev/hdc1

---

### Post by Anakist on 2007-01-03
I found no errors on the GParted Live CD. it saw the HDDs fine and when I did that from the terminal it just gave me the info and said be sure to do a test with the -n and -s option before resizing. Then I told it to check and repair the two disks which took 2secs for the 200g and 1sec for the 20g.

Did checkdisk through Xp and Gparted on my machine says the same thing still.

Any other ideas?

James

---

### Post by logos34 on 2007-01-03
Can't you people keep more sensible hours? ;-) from GMT-6 time zone

Ok, if you're not getting any more error messages, then you can edit your fstab and try to mount them.

Mount
For the sake of consistency I'd create two new mount points named '/media/hdc1' and '/media/hdd1', or '/media/windows2' and '/media/windows3' (because these are your 2nd and 3rd windows partitions respectively).  Or if you prefer use '/mnt/<name>', '/mount/<name>', etc.  

To make sure there are no mount points by that name already:
> ls /media/hdc1
ls /media/hdd1
 
It should come back 'No such file or directory'.  

Then,
> sudo mkdir /media/hdc1
sudo mkdir /media/hdd1

Fstab
Now you need to add them to the end of your fstab file.  

Just use the same options as your main ntfs partition on hda1.

Backup your fstab file first:
> sudo cp /etc/fstab /etc/fstab.backup 

Then 
> sudo gedit /etc/fstab

To the end you would add:
> /dev/hdc1 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
/dev/hdd1 /media/hdd1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0

Replacing the '1' at the end with '0' tells fsck to ignore that filesystem (the correct setting.  Don't know why Ubuntu defaults to '1'...)

(defaults = *rw, suid, dev, exec, auto, nouser, and async).

	(*obviously on ntfs partitions it's actually 'ro'--read-only')

Save changes and close. The 'auto' above is for automount at startup.

Then manually mount all your partitions:

> sudo mount -a

List mounted partitions
> mount

Ctrl+Alt+Backspace to restart.

Post back with the results!

For more info:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28mount%29](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28mount%29)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mount%29](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mount%29)
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)
[https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)
[https://help.ubuntu.com/community/MountNtfsOnBoot?highlight=%28mount%29](https://help.ubuntu.com/community/MountNtfsOnBoot?highlight=%28mount%29)

---

### Post by logos34 on 2007-01-03
oh, and post the output of this:
> ls /dev/disk/by-uuid/ -alh

It'll show if edgy generated a UUID for hdc1 and hdd1 when you hooked them up.  If so, you could append the # to the beginning of the fstab entry just like for the other partitions.

---

### Post by Anakist on 2007-01-04
Nada. Didn't work.

> **logos34 said:**
> oh, and post the output of this:


It'll show if edgy generated a UUID for hdc1 and hdd1 when you hooked them up.  If so, you could append the # to the beginning of the fstab entry just like for the other partitions.

total 0
drwxr-xr-x 2 root root 120 2007-01-04 16:37 .
drwxr-xr-x 6 root root 120 2007-01-05 02:37 ..
lrwxrwxrwx 1 root root  10 2007-01-04 16:37 1E78143778140FDF -> ../../hdc1
lrwxrwxrwx 1 root root  10 2007-01-04 16:37 306601D466019C2A -> ../../hdd1
lrwxrwxrwx 1 root root  10 2007-01-04 16:37 6E703EB5703E83BD -> ../../hda1
lrwxrwxrwx 1 root root  10 2007-01-04 16:37 8b5556b3-30c5-4ba1-9ef8-ed4de9ae0360 -> ../../hda2


From the sudo mount -a and mount

james@BeAsT:~$ sudo mount -a
[mntent]: line 12 in /etc/fstab is bad (UUID=1E78143778140FDF /dev/hdc1 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0)
[mntent]: line 13 in /etc/fstab is bad (UUID=306601D466019C2A /dev/hdd1 /media/hdd1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0)
james@BeAsT:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

James

EDIT: I keep good hours! You bloody yanks think you own the world! ;)

---

### Post by logos34 on 2007-01-04
Can't sleep...bad thunderstorm tonight...So it looks like I'm now the one keeping odd hours!
Let's check my email...

> [mntent]: line 12 in /etc/fstab is bad (UUID=1E78143778140FDF /dev/hdc1 /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0)
[mntent]: line 13 in /etc/fstab is bad (UUID=306601D466019C2A /dev/hdd1 /media/hdd1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0)

Sorry, my instructions were misleading:  the UUID actually goes BETWEEN '/dev/hdx' and the mount point '/media/hdx'.  Look at your fstab:
> # /dev/hda2
UUID=8b5556b3-30c5-4ba1-9ef8-ed4de9ae0360 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1
UUID=6E703EB5703E83BD /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda3
UUID=84e107b8-0613-4ecb-9808-856103240edc none swap sw 0 0

Each uuid is for the device immediately above it.  So just replicate your existing entries.  Make it look like this:

#/dev/hdc1
UUID=1E78143778140FDF      /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
#/dev/hdd1
UUID=306601D466019C2A     /media/hdd1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0

Hopefully that'll work.  

Post your fstab.

---

### Post by Anakist on 2007-01-04
It is what? 2am there? I was surprised when I saw a reply! Instead of being in bed, you are connecting delicate electronic equipment to the power supply during a storm? Sweet!

FSTab is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8b5556b3-30c5-4ba1-9ef8-ed4de9ae0360 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6E703EB5703E83BD /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=84e107b8-0613-4ecb-9808-856103240edc none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

New one will be:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8b5556b3-30c5-4ba1-9ef8-ed4de9ae0360 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6E703EB5703E83BD /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=84e107b8-0613-4ecb-9808-856103240edc none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hdc1
UUID=1E78143778140FDF /media/hdc1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
#/dev/hdd1
UUID=306601D466019C2A /media/hdd1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0


James

---

### Post by logos34 on 2007-01-04
Alternatively, just forget the uuid, take out the '#' and make it look like this:
> /dev/hdc1	/media/hdc1 	ntfs 	defaults,nls=utf8,umask=007,gid=46 	0 	0
/dev/hdd1	/media/hdd1 	ntfs 	defaults,nls=utf8,umask=007,gid=46 	0 	0

(for the spaces shown above hit the Tab key once)

*You just missed me...You were online when I last posted...You might want to subscribe to this thread ('Thread Tools' top of page) and enable 'instant notification' by email.  A yellow sun next to a poster's name means he is currently logged in to the forums.

---

### Post by Anakist on 2007-01-04
YOU ARE A LEGEND!!!!!!!!!!!!!!!!!!!!!!!

All works now. Thank you very very much!

James

---

### Post by logos34 on 2007-01-04
> It is what? 2am there? I was surprised when I saw a reply! Instead of being in bed, you are connecting delicate electronic equipment to the power supply during a storm? Sweet!

Oh sh*t! That reminds me--I don't have a UPS backup power supply for this pc (it's on the other machine)...Please no blackout!

So can you mount them?

---

### Post by logos34 on 2007-01-04
> YOU ARE A LEGEND!!!!!!!!!!!!!!!!!!!!!!!

All works now. Thank you very very much!

Thank you kindly!  Glad everything worked out.

---

### Post by Anakist on 2007-01-04
Yep all mounted and working. I just have to work out how to get mp3 playing ad figure why sound is gone and I will be right.

Enjoy your storm, we don't get enough of them over here anymore!

James

---

### Post by logos34 on 2007-01-04
> just have to work out how to get mp3 playing ad figure why sound is gone and I will be right.

Enjoy your storm, we don't get enough of them over here anymore!

There's always one thing or another left to get working in linux....

I guess I'll quit while I'm ahead and catch some more zzz's...

over and out

(don't hesitate to post again if you have any problems).

---

