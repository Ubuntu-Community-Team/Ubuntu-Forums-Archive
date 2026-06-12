---
title: "how do I change an automount point?"
date: 2007-01-17
forum: General Help
---

### Post by rudyj on 2007-01-17
I have an external hard drive that is connected to the computer via an enclosure that uses a USB 2.0 connection.  When I connect the device it is automounted at /dev/hda2.  The only problem is I have a partition that is also mounted at /dev/hda2. So if I have the enclosure connected while I'm booting Ubuntu, the partition does not show and the enclosure takes it's place.  Here is my fstab in case I need to change something:

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=6e82c536-2bdc-45a6-ae80-93fa065d7545 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=220CFF700CFF3D7B /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=1E3C2A403C2A12F7 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=2a8047dc-15f2-4117-a61a-97102a93e574 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hda4    /home/rudy/Desktop/Shared vfat  iocharset=utf8,umask=000  0    0
[/PHP]

I've tried changing the mount point of the partition to something like hda3, but the enclosure then automounts to hda3 as well!

So my basic question is this, how do I get the enclosure to automount elsewhere so it doesn't interfere with the partition?

---

### Post by dcstar on 2007-01-17
> **rudyj said:**
> I have an external hard drive that is connected to the computer via an enclosure that uses a USB 2.0 connection.  When I connect the device it is automounted at /dev/hda2.  The only problem is I have a partition that is also mounted at /dev/hda2. So if I have the enclosure connected while I'm booting Ubuntu, the partition does not show and the enclosure takes it's place.  Here is my fstab in case I need to change something:

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=6e82c536-2bdc-45a6-ae80-93fa065d7545 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=220CFF700CFF3D7B /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=1E3C2A403C2A12F7 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=2a8047dc-15f2-4117-a61a-97102a93e574 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hda4    /home/rudy/Desktop/Shared vfat  iocharset=utf8,umask=000  0    0
[/PHP]

I've tried changing the mount point of the partition to something like hda3, but the enclosure then automounts to hda3 as well!

So my basic question is this, how do I get the enclosure to automount elsewhere so it doesn't interfere with the partition?

Try giving the enclosure a volume label.

---

### Post by rudyj on 2007-01-18
Thanks for the reply!  I'm pretty new to Ubuntu, would you mind showing me how to go about giving it a volume label?  Thanks!

---

### Post by bodhi.zazen on 2007-01-18
See this thread, go to the label section :p

[http://www.ubuntuforums.org/showthread.php?&t=283131](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by rudyj on 2007-01-19
Thanks I'll try that!  Under the labels section I see lables for various file systems but I don't see one for ntfs.  Is it in there somewhere and I'm just missing it?

---

### Post by bodhi.zazen on 2007-01-19
First install ntfsprogs:```
sudo aptitude install ntfsporgs
```Or use Synaptic.

Then:

Show label:```
ntfslabel <device>
```

Change label:```
ntfslabel --new-label <device>
```

Where <device> = your partition to label (/dev/hda1 perhaps :p )

I'll update my how-to on fstab ;)

---

### Post by rudyj on 2007-01-19
Thanks a lot that worked!  

One thing though, in your directions I tried to do:

ntfslabel --new-label <device> 

but this did not work, to give the device a label I had to do:

ntfslabel <device> <label>

where my label was usb

It said --new-label would not work.  

Thanks a lot though, this makes things a lot more convenient for me.

---

