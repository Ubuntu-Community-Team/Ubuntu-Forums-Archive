---
title: "Lost HDD, cant boot"
date: 2007-03-08
forum: General Help
---

### Post by recon69 on 2007-03-08
Hi, 
   Been using Ubuntu 6.06 for about 6 months now, been great but hit a big problem. My DVD drive stopped working and while I was tring to check out what was wrong with it I managed to lose access to one of my hard drives( I did not change any settings so not sure why it stopped working). HDD was mounted as the /home dir, now I can only boot ubuntu to the command line, I can get gnome to the login screen but when i login my session crashes as gnome cant find my user dir ( home/mec ). I have no idea what happened to the HDD ( I got 3 HDD's in my computer, one has windows and ubuntu on it, one is a fat32 with my shared data, the last was mounted as the home dir. the DVD is dead and I will have to get a replacment but the HDD seems ok but has no data ( I might be wrong here as ubuntu might not be mounting it and showing me a totaly different home dir).

So, as this is the first time I have trouble shot a HDD in ubuntu I was wondering what people would recommend. Sorry about the lack of specific info but as I can only boot to windows it really slow having to boot up every time i want to check somthing but if anyone can give me a list of cmd line commands to run I can post the results. 

Regards

---

### Post by Heliix on 2007-03-08
that's strange.. it sounds like a hardware problem, but I may be wrong.
check your /etc/fstab and check the available harddiscs, i.e. devices in /dev/*. does the device you want to mount to /home exist? and do you mount it with write permissions?
or, are you able to mount it manually (as root)?

the only time when my laptop argued it can't mount /dev/hda was when the harddisc was damaged (and all data lost :( ), I hope this is not your case.

---

### Post by recon69 on 2007-03-15
Hi, 
  Sorry about the delay but my net connection has been down for the last week, stupid phone company. anyway ...

Did a bit of checking , first here is my fstab 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults             0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw                   0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto      0       0
/dev/hdb1       /media/hdb1     vfat   defaults,uid=1000,gid=1000            0      1
/dev/hdc2       /home           ext3 nodev,nosuid            0       2 
```


and a 
```
> ls \dev\hd*

hda   hda1   hda2   hda3   hdb   hdb1   hdc   hdc1   hdc2   hdb 
```

and 

```
sudo mount /dev/hdc2 
wrong fs type , bad option , bad superblock on /dev/hdc2 
```

and fininaly 

```
dmesg | tail 
  ext3: No journal on filesystem on hdc2 
```


so, I going to have a look around to see if i can repair the superblock on that drive. any help welcome. 

Regards

---

### Post by Xappe on 2007-03-15
maybe unmount the drive and run a fsck on it

---

### Post by recon69 on 2007-03-21
well I got it fixed , 

used 
  > e2fsck -b 32768 /dev/hdc2 

had a bad inode 8 in my journal , the command removed the journal and fixed some sectors. then i changed my fstab entry for hdc2 to ext2. 

got the info from this page 

[http://www.mrctr.upmc.edu/mrrc/computing/linuxguide](http://www.mrctr.upmc.edu/mrrc/computing/linuxguide)

thx for the help

just got to figure out how to put the journal back. but am happy for the moment just having ubuntu back

---

### Post by Xappe on 2007-03-21
you should be able to do that with tune2fs:

```
$ tune2fs -j /dev/hdc2 
```
with the drive not mounted (maybe from a livecd).

Then remount the partition as ext3.

---

