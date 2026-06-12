---
title: "NTFS Drives [Hardy]"
date: 2008-06-04
forum: General Help
---

### Post by Depressed Man on 2008-06-04
For some odd reason my NTFS drives are not auto mounting on start up after I reinstalled Ubuntu. Yet on my laptop it automounts, do I have to setup something to have them automount on startup/login?

Edit: My issue is solved, however I am keeping this thread open for bujutsukai (see post #6).

---

### Post by danwood76 on 2008-06-04
They need to be added to your fstab.
We can help you configure this if you post the output of the following commands in the terminal:

```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by prince_niceguy on 2008-06-04
are they in fstab? if there is some problem with ntfs then login into windows and do a shutdown and then boot in ubuntu. they should mount.

---

### Post by xfceuser on 2008-06-04
see if have shut down windows properly, reboot into windows and shut down from the windows.

---

### Post by leito666 on 2008-06-04
You could install:

sudo apt-get install disk-manager


That will add the necessary lines to fstab

---

### Post by bujutsukai on 2008-06-04
I have a similar problem.  I have a portable hdd that is formatted NTFS because I used to use windows.  I have movies and music loaded on it.  I would like to access from my laptop (Ubuntu 8.04), but I get a series of error messages ranging from can't mount to I don't have privileges to access it.  Is all lost?  This is from my fstab:

/dev/sdb1 /media/Backup%20and%20Media ntfs-3g force 0 0

The %20 are there because it was breaking due to the space in the drive name.  Any help?

Also, I wasn't able to install disk-manager as above.  Something about it not being found.

---

### Post by zekica on 2008-06-04
To last post: have you tried using \040 instead of %20. I think it is a correct way to insert spaces in fstab.

---

### Post by bujutsukai on 2008-06-04
Well, I just tried it, and got this message:

You are not privileged to access...Backup and Media.  

It's a step forward, but it seems like there are no more steps?  Crap I hate windows more and more...

---

### Post by Gannon8 on 2008-06-04
All I had to do was:
```
sudo mount -f ntfs /dev/hda1 /windows/
```
(Change directories as necessary)

---

### Post by bujutsukai on 2008-06-04
I'm sorry--I'm not very good at this, apparently.  Everytime I try to run the mount command, I get this drivel:

thomas@thomas-laptop:~$ sudo mount -f ntfs /dev/sdb1 /media/Backup\040and\040Media/
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by Gannon8 on 2008-06-04
> **bujutsukai said:**
> I'm sorry--I'm not very good at this, apparently.  Everytime I try to run the mount command, I get this drivel:

thomas@thomas-laptop:~$ sudo mount -f ntfs /dev/sdb1 /media/Backup\040and\040Media/
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

I think I got that when the drive was already mounted...
Type mount by itself and see if it's mounted under /windows/ or something like that.

---

### Post by danwood76 on 2008-06-04
that should be mount -t
-f is a nonsense switch and is why its moaning at you.

so:
```

sudo mount -t ntfs /dev/sdb1 /media/Backup\040and\040Media/

```

---

### Post by bujutsukai on 2008-06-04
I think it IS mounted, because it shows up in my "Places."  However, when I click it I get the "You are not privileged" message.

This, from the "mount" command:

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
none on /proc/bus/usb type usbfs (rw,devgid=1004,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

I can't say that I see it there, though we're way past my level of comfort ;-)

---

### Post by danwood76 on 2008-06-04
Devices listed in your fstab will not automount, also if its in your fstab and is NTFS you cannot mount as a normal user by clicking it in places, this is a bug with the ntfs-3g driver.

Just remove its entry in the fstab, reboot, and insert the USB drive.
If the drive doesnt mount automatically you need to make sure in windows that you unmount it before unplugging it.

ALso the lines in your fstab is bad, forcing the drive to mount is not reccomended with ntfs as it is a journaling system and needs to be unmounted properly.

---

### Post by Depressed Man on 2008-06-05
> **danwood76 said:**
> They need to be added to your fstab.
We can help you configure this if you post the output of the following commands in the terminal:

```

sudo fdisk -l
cat /etc/fstab

```

Sorry for the delay, I was out of the house for the rest of the day. Here is the output.

For sudo fdisk -l

```
 sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98349834

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19124   153613498+   7  HPFS/NTFS
/dev/sda2           19125       36483   139436167+   f  W95 Ext'd (LBA)
/dev/sda5           19125       33841   118214271    7  HPFS/NTFS
/dev/sda6           33842       33957      931738+  82  Linux swap / Solaris
/dev/sda7           33958       36483    20290063+  83  Linux

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000be65a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2       36481   293025600    f  W95 Ext'd (LBA)
/dev/sdb5               2       36481   293025568+   7  HPFS/NTFS

```

and for cat /etc/fstab

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=0fb5df19-8fc3-49b9-8404-cd2531000fa4 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=dac4d363-1fc6-4cfa-87dc-b2f46a4c620e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```

---

### Post by danwood76 on 2008-06-05
Ok so you have 3 NTFS partitions.
In my example below I will call them NTFS1, NTFS2, NTFS3.
You can call them what you like, whatever you call them will be the name they get on the desktop, avoid using spaces as the fstab wont like it.

So first create the mountpoints for the partitions:
```

sudo mkdir /media/NTFS1
sudo mkdir /media/NTFS2
sudo mkdir /media/NTFS3

```
Then open up the fstab for writing in gedit (need root access):
```

sudo gedit /etc/fstab

```
Then add the following three lines to the bottom:
```

/dev/sda1 /media/NTFS1 ntfs-3g defaults 0 0
/dev/sda5 /media/NTFS2 ntfs-3g defaults 0 0
/dev/sdb5 /media/NTFS3 ntfs-3g defaults 0 0

```
Save the fstab and to check that it mounts ok run:
```

sudo mount -a

```
Your drives should then appear on the desktop.

---

### Post by Depressed Man on 2008-06-05
Thank you, it's automounting now. Any idea why it wasn't before though (for future knowledge?)

---

### Post by muteXe on 2008-06-05
Because Hardy is a backwards step in Ubuntu development.  Only in my opinion of course.

---

### Post by bujutsukai on 2008-06-05
Thanks Danwood.  I went to a windows machine and it won't even read there now.  I think I've lost the drive, both literally and figuratively.  Thanks for your help.

---

### Post by danwood76 on 2008-06-05
@Depressed Man (and muteXe)
Linux filesystem management has always been done like this.
The difference between gutsy and hardy is that in hardy there is a piece of software that is supposed to detect partitions that arent auto mounted, and tell you theyre there and offer to automount.
I remember this working in the beta.
It obviously doesnt work now, or if it does not very well.
In gutsy such partitions were added to the fstab during install by the installer.

@bujutsakai
Editing the fstab doesnt affect your drive, merely a text file on your main linux partition.
Are you sure the drive isnt just dead?
Also blaming me is stupid, its obviously something you've done.
Anything you have done in software can be reversed but if the drive has a hardware failure then its borked!

-- edit --

Also if the filesystem is dead its probably to do with the fact you were forcing it to mount each time as opposed to safely removing it and keeping the ntfs journal correct.

---

### Post by muteXe on 2008-06-05
> **danwood76 said:**
> 
I remember this working in the beta.
It obviously doesnt work now, or if it does not very well.
In gutsy such partitions were added to the fstab during install by the installer.



So you wouldn't class this as a backwards step then?

---

### Post by danwood76 on 2008-06-05
Yeah I suppose it is. :)

I've always done it through the fstab file with a text editor, I guess some sort of GUI would be good and would also solve a lot of threads posted on here about automounting.
I'm sure I saw some sort of GUI in the alpha, maybe not the beta but I guess it was unstable or something as in why it got removed. (or maybe I was dreaming)

---

### Post by Depressed Man on 2008-06-05
I will keep this thread open till the other poster gets their issue resolved.

---

