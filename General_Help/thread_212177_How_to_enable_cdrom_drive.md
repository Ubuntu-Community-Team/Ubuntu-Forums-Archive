---
title: "How to enable cdrom drive?"
date: 2006-07-09
forum: General Help
---

### Post by usp8riot on 2006-07-09
I go to "System Settings", then "Disk & File Systems", and /dev/hdc is disable. I try to enable as administrator and get this message;

 "An error occurred while enabling /media/cdrom.
The system reported: mount: No medium found"

In other words, I know I don't have a cd in there but it won't let me open my cdrom drive to put a cd in there. Am I missing something or is the drive just not working? Thanks in advance.

---

### Post by OpsVentus on 2006-07-09
Hello,

it's not quit clear to me what you are trying to do. Are you trying to eject your cd-drive by clicking enable in the disk & file systems? 
This will not work. To eject your cd-drive you can just click on the button of your cd-drive. Or is this not working?

Cheers,
Bart.

---

### Post by usp8riot on 2006-07-09
Oops, sorry, I'm running Kubuntu 6.06, wrong forum. Anyhow, maybe it's not much different than 5.10. But I'm trying to eject my CD drive to put a CD in but it's not working. I remember it working in Windows so I'm wondering if Kubuntu just doesn't recognize it. It's only a few years old.

---

### Post by OpsVentus on 2006-07-11
To eject your cd-drive push the button on your cd-drive.

---

### Post by usp8riot on 2006-07-11
Thanks Ops, and all this time all I had to do was push the button thingy on the drive thingy.

Seriously, it doesn't work. Maybe it's a mount problem.

---

### Post by OpsVentus on 2006-07-12
Well, now we have established what the problem is:
What does mount say?
(goto terminal and type 'mount')
And can you unmount the drive?
(goto terminal and type 'sudo umount /dev/hdc' / 'sudo umount /media/cdrom')
And what does your fstab look like?
(goto terminal and type 'gedit /etc/fstab')

---

### Post by bikeboy on 2006-07-12
More than likely this will work. Places > Computer > Right click CD-Drive > Eject. When the cd has been mounted it won't let you eject using the button, just in case it shouldn't be unmounted suddenly.

---

### Post by usp8riot on 2006-07-12
Thanks, that got it. I had to software eject. I had a problem with the fstab also and just now figuring the mount stuff out.

---

### Post by oikakzo on 2007-08-04
> **bikeboy said:**
> More than likely this will work. Places > Computer > Right click CD-Drive > Eject. When the cd has been mounted it won't let you eject using the button, just in case it shouldn't be unmounted suddenly.
Hey, thanks for the help. I accidentally installed Ubuntu yesterday, out of curiosity.. and so I'm stuck with it..

---

### Post by Cubby on 2008-01-25
Hi,

I am having the same problem as I have recently switched to Kubuntu 7.10 and only now was hinted to this problem after I nstalled  k9Copy, and in k9Devices folder, the k9cddrive.cpp file states:
canReadDVD=false
canWriteCDR=false
canWriteDVD=false
device=""
name=""
ifdef HAVE_HAL
m-Device=NULL

So, I did the following in terminal:

```
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/hdb3 on /home/me/<mount point> type vfat (rw,uid=0,gid=0)
```

and also ran this 
sudo mount /dev/hdc
mount: No medium found

as well as
sudo mount/media/cdrom
mount: No medium found

and in kate /etc/fstab it shows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=3bd06458-70ee-4be7-8543-d474ca9b162a / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hdb5
UUID=49180f4f-c38d-4e35-9acc-9b5bc776c7ae none swap sw 0 0
/dev/hdd /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0
/dev/hdc /media/cdrom1 auto users,atime,auto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdb3 <mount\040point> vfat noauto,uid=0,gid=0,auto,rw,nouser 0 0 

If I go to system settings > Advanced > Disk & Filesystems

the screen shot is what is shown in the attachement. 

If I try to enable these I get the error : An error occurred while enabling /media/cdrom1.
The system reported: mount: No medium found.  

Thanks for reading over my post.  

Lisa Marie

P.S.  I did change the 19G partition from Auto to vfat, as it is a fat32 partition that I also use for my dual-OS windows 2k.

---

### Post by Cubby on 2008-01-25
here is some additional information when I Insert a cd, open a terminal and type:
 sudo mount, as well as sudo mount /dev/cdrom
 sudo mount /dev/scd1
 sudo mount /dev/dvd
 and
 cat /etc/fstab /etc/mtab

One thing I notice is I do not get any sound from my system due to this problem.  From the below code I am wondering is I should change type from auto to iso in the disk & filesystems settings.

```

/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
me@me:~$ sudo mount /dev/cdrom
mount: No medium found
me@me:~$ sudo mount /dev/scd1
mount: can't find /dev/scd1 in /etc/fstab or /etc/mtab
me&me:~$ cat /etc/fstab /etc/mtab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=3bd06458-70ee-4be7-8543-d474ca9b162a / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hdb5
UUID=49180f4f-c38d-4e35-9acc-9b5bc776c7ae none swap sw 0 0
/dev/hdd /media/cdrom0 iso9660  0 0
/dev/hdc /media/cdrom1 iso9660  0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdb3 <mount\040point> vfat uid=0,gid=0,auto,rw,nouser 0 0
<device> /media/floppy0 auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/hdc /media/cdrom1 auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/hdd /media/cdrom0 auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
me@me:~$
```

Thanks to anyone that takes a look.

A few days later and I am still at a mount cdrom standstill.  I decided to reinstall ubuntu fiesty fawn and see what /etc/fstab says in this OS.

fstab results for ubuntu feisty fawn

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=20cdcd33-0985-4b0e-b79c-5356c43e6135 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=806df295-2d1e-406f-8f32-4caaa099cf28 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

updated to add that I can't mount the optical drives here, either.

---

### Post by Cubby on 2008-01-28
In ubuntu, I'm still having mount cdrom problems.

When I type sudo mount /media/cdrom or sudo mount /dev/cdrom I get the following

```
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

As you can see from the screen shot, it shows moint point mount system mount options as not mounted.  What should I add to these fields, if this is what I need to do. 

this is what dmesg | tail shows

```
 dmesg | tail
[ 6719.267098] ide: failed opcode was: unknown
[ 6719.267867] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[ 6719.267874] end_request: I/O error, dev hdc, sector 64
[ 6719.267890] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[ 6849.339607] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[ 6849.339618] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[ 6849.339622] ide: failed opcode was: unknown
[ 6849.340067] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[ 6849.340075] end_request: I/O error, dev hdc, sector 64
[ 6849.340329] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
```

Thanks for looking over my problem.  I really appreciate it.

Lisa Marie

a few hours later, and I found out it is probably because I was inserting an audio CD in my drive.  When I inserted the ubuntu installation disc, it showed as mounted, and had as option to unmount.  So, from what someone else said, "Audio CD's don't count because, as far as I know, they need not be mounted. I'm sure you installed Gutsy from some media, but it would still be nice to check the CD with some data CD's." and , "  I did this, and got my answer.

---

### Post by DMK62 on 2008-01-28
Hi

Found the mount issue post you mentioned in another thread.

Do you have more than one optical drive on the computer ?

on kubuntu

kdesu kate /etc/fstab

I only have one optical drive and the entry I have that works is :

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

It is located after the hard drive partitions listed in fstab.

To reload fstab you can use the command

sudo mount -a 

or you can just restart the computer.

hth 

Dale

Ubuntu and Kubuntu are a bit different when media is inserted. KDE allows you to configure plugins to perform certain actions depending on what type of media is inserted. You can fine tune that through the KDE Control Center ( enter kcontrol from the terminal to access it ). You can add a menu entry for Kcontrol by right clicking on the K Menu and opening Menu Editor and in Menu Editor go to File > New Item and give it a name, for the command browse to /usr/bin and look for kcontrol and click on that and then File > Save and quit the Menu Editor.

---

### Post by Cubby on 2008-02-01
Hi Dale!

Thanks so much for this information.  Well, I'm back to trying out kubuntu 7.10 Gutsy, and I'm laughing somewhat as I'm getting no sound, as was the discussion at the other thread.  I did from the live CD, but not the installed OS.  So, this is totally different from my mount problem, and I'm about to post a new topic on it.  

I do appreciate your help with the problem I posted in this thread (piggy-backed the topic).  

Since I am here in this thread, I will let you know what occurs when I insert the kubuntu boot disc in my master DVD read write  - a KDE Daemon window pops up, asking "a new medium has been detected.  What do you want to do". "Medium type unmounted cd writer".  I click cancel.  Then I go to the disc icon and right click on it and click on "mount" and it takes a few seconds, and the icon changes to kubuntu and shows the little green arrow pointing towards the s.e.  So, it is mounted.   If I click on properties and under "general" tab, it says at top "Properties for hdc"...mounted cd writer...contents folder...location /(media).  Permissions tab says owner - group - others "can view content". Ownership - root.
Under meta info tab it shows...file:///media/cdrom0...device node /dev/hdc 
and under Mounting tab it is all grayed out.  There is a choice under "general mount options" to tick "mount automatically", but as it is grayed out, I cannot tick this and don't know how to change this as user or root, or if I even should change this.

I'm not sure, but I think I want to have this master dvd writer mount automatically so when I finally get around to installing programs like cd burners or k9copy, it will be mounted and the files in this programs will show it as detecting the device.  As you can tell I'm a bit confused about having these devices automatically mount as they do in windows.  I also notice in Amarok that I have to manually set the device for Media Device Browser, and when you click "connect" button, I don't know what to enter in the "pre-connect command" field.  But, this is another question.  Like I said, I'm unsure if these devices need to be always mounted for the programs that use them to work properly.

I have two cdroms, the master is a dvd read writer (cdrom0) and the slave is the asus dvd reader (cdrom1) as shown in the thumbnail.  

My fstab is showing currently:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=d04affad-5d8e-4841-9fd9-d15d28fae2d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=40d01108-920a-486b-8db3-cec4ebe00371 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```
so now for some reason my kubuntu fstab looks normal, the same way it looked like in ubuntu feisty fawn.  

Well, back to my first problem.  I need to start another thread about it. 

Again, thanks for your time.  

Lisa Marie

---

