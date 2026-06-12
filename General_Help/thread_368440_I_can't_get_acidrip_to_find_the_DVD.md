---
title: "I can't get acidrip to find the DVD"
date: 2007-02-23
forum: General Help
---

### Post by billdotson on 2007-02-23
right now I cannot even get acidrip to find the DVD. the default for acidrip is /dev/dvd and it says "no DVD found.. is there a DVD in the drive?" My fstab looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=c51e7206-7183-4cee-b79f-142eb72cbc1b / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb2
UUID=1e0d2ef5-41dc-4288-8518-4814ecc5c585 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
/dev/sda1 /home/sgtmattbaker/Windows_NTFS ntfs nls=utf8,umask=0222 0 0

I have tried /dev/hda and it says that that is not a valid DVD drive.

What is the best dvdripper and transcoder?  does dvdrip work better than acidrip (mencoder frontend) or should I keep using vobcopy?  The only thing is I want to be able to transcode the video and audio to something other than mpeg2 and ac3 but I don't know if you can do that with vobcopy (and transcode I think)

---

### Post by DagMan on 2007-02-24
I wish I knew this too but  it isn't a persistant problem for me.  You can try copying the DVD to an empty folder and then pointing acidrip at the folder instead of the device.  I've had that work but don't remember if it's worked in the scenario when the DVD could not be seen.  It's worth a shot... and if it works hopefully it will do the next step properly and do crop detection properly.

---

### Post by MattressVon on 2008-05-16
Solution: change /dev/dvd to /dev/dvd1 it really is that simple. if you have SATA disc drives your sata ports are named in pairs with the even numbers proceeding the odd. ie. if you plug one sata drive into sata 01113 and one into 01112, 01112 will be /dev/dvd and 01113 will be /dev/dvd1 if you only plugged in one disk drive on your board and it is on an odd port, it will still be /dev/dvd1. i have no idea why this is, but that's the way it is.If your disk drive is IDE you can ignore this but if it's SATA try this out. Also try other numbers as some boards have the /dev ports numbered in order from 0 (or just /dvd)to what ever the max number of sata ports are.

---

### Post by coyotepod on 2008-07-18
i recently had to change mine to /media/<dvd name>. For example, /media/OFFICE  I didn't have to do this before. I have to name the DVD specifically as well or it doesn't load. I'd like to change it to something more generic so it autoloads everytime.

---

