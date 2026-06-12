---
title: "external usb hdd mount problem"
date: 2007-06-19
forum: General Help
---

### Post by drew boardman on 2007-06-19
Hi, 
External 40gb HDD won't mount.  It did now it won't.  I can't see it at all but it works under Windows.  I've not played the partition, I just store the family photos on it.

Any ideas on how I can 
1. see it
2. mount it

Thanks

Drew

---

### Post by warcriminal on 2007-06-19
The drive is most likely formatted as NTFS.  If that's the case then you need to use something like ntfs-3g to make it visible and usable in Ubunut.

There is a guide here;

[http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux](http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux)

It talks about a network volume, but just substitute the network info for a local drive, so instead of //servershare use /dev/sda2

---

### Post by drew boardman on 2007-06-20
Thanks for the response  but it is FAT32, will the ntfs-3g still work?

DRew

---

### Post by drew boardman on 2007-06-20
Hi, 
I do not know wat i have done but it now appears in Nautilus.  I cannot mount though!

Heres the fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=77e15c80-11e1-4f61-b256-1e97b4fc7c35 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3898876c-5a28-4617-af0d-8f1a824b4ec8 /home           ext3    defaults        0       2
# /dev/hdc5
UUID=1d1b77ea-ed59-46a4-b086-c3c998df70b9 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/USB  auto    rw,user,noauto  0       0

Thanks  Drew

---

### Post by logos34 on 2007-06-20
> **drew boardman said:**
> Thanks for the response  but it is FAT32, will the ntfs-3g still work?

DRew

$ gnome-volume-properties

are the first 3 boxes ticked?

check /etc/fstab too.  might need to add a vfat entry

---

### Post by drew boardman on 2007-06-20
Hi, 

First 3 boxes checked.
Where in the fstab line do I add vfat?
And the error msg when attempting to mount the drive is; "mount: mount point /media/usb does not exist".  Sorry should have perhaps mentioned that earlier.

Thanks

Drew

---

### Post by logos34 on 2007-06-20
it's '/media/USB'

but where's there partition number(?)
> /dev/sdb? /media/USB auto rw,user,noauto 0 0


try
> sudo mount /dev/sdb1 /media/**USB**

create a mount point if need be:

sudo mkdir /media/USB

Or try adding this alternative entry to fstab:
/dev/sdb1 /media/fat32 vfat defaults,umask=0000 0 0

create new mount point (called, for example, 'fat32'):
sudo mkdir /media/fat32 

sudo mount /dev/sdb1 /media/fat32

---

### Post by terrellf on 2007-06-20
Hi,

It appears to be a very common problem reading back thought the forums.  But I could not find the fix.  I have Ubuntu 7.04 dual boot with XP.

I have a Seagate external drive I plugged in but it was NTFS and I did not have ntfs-3g loaded.

I tried to unmount the drive but it would not let me since it wanted to transfer files to the disk but could not do to the NTFS without the ntfs-3g loaded, so I pulled the plug out on the drive.

I loaded ntfs-3g with Synaptic and it now sees the other NTFS partitions on the internal drive fine.

But it will no longer "see" the Seagate USB external drive when plugged in.

I put the drive on an XP machine and did check disk and all that but there were no apparent problems.  I tried the drive with Xbuntu and win2000 on a different machine with no problems.

But Ubuntu (7.04) does not load or even acknowledge that the drive exists now.  It did mount it the first time even if it could not read NTFS.  I tried lsusb and get this with the USB drive connected.

> Bus 005 Device 008: ID 0bc2:3000 Seagate RSS LLC 
Bus 005 Device 002: ID 04a9:2213 Canon, Inc. LiDE 50/LiDE 35
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

I pulled out the USB drive plug and now get this:

> Bus 005 Device 002: ID 04a9:2213 Canon, Inc. LiDE 50/LiDE 35
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  


So Linux knows it's there and it is connected and reporting fine...

So seems like a software problem:p  

I don't know enough about LINUX but I would guess some file got corrupted and some pointer to load the Seagate USB disk has gone bad.  Two other USB pen drives and the printer and scanner still work fine.  Some have mention the fstub file or "mounting point" being corrupted but I don't know about that...

Hope this helps some...  If anyone wants to see files or have me check something, be specific as to where they are and what buttons to push since I am not very familiar with LINUX but I do know enough to be dangerous ;)

Terry

---

### Post by drew boardman on 2007-06-21
Sorry, none of the above worked.  Its still sits there in the file manager but unable to mount.

Any more ideas, I getting desperate.

Thanks

Drew

---

### Post by terrellf on 2007-06-21
interesting...

I went to System>Administration>Synaptic Package Manager and installed "gparted".

Then go to System>Administration and "Gnome Partition Editor" shows up.

Open that program and on the top right selection box you can select your USB drive (/dev/sdb/)!!

298 GiB ntfs drive and all....  Now to see if it can be mounted...  It is actually /dev/sdb1 .

Not sure what it all means or how to fix anything.  But the drive and file system is being detected perfectly fine and the base level of software and the hardware is fine.  It is a higher level program problem...  Some forums point to a "pmount" bug...

Terry

UPDATE:  Did it!!!!!!!!!

From the above Gnome Partition Editor program I found that the USB drive is "/dev/sdb1".  No other fdisk -l or lsusb junk would tell me that before :p

Then apparently you need a "mount point" for it so I just made up the name "usbdrive1" since that was new and unused.  This will be what the drive is called on the desktop icon.  It can probably be any name you wish.

Then the magic command is:

> sudo pmount /dev/sdb1 usbdrive1

Then it pops up and works fine on the desk top just like nothing was ever wrong.....  Have not tried to reboot or anything till I get this written down...

So the problems are:
1. It messed all up in the first place.  Mounting file or setup must have been corrupted for when that particular device was plugged in and the program was not able to retry or reset and try again.  So it just dies....

2. Trying to find the USB drive is "interesting".  The "modern" Ubuntu seem too weak or restricted to search the lower levels for a lost drive.

3. Trying to find the exact device name "/dev/sdb1" is not easy and it took on older program install (gparted) to do it "very easily"...  It was trivial for the old program...  Seems impossible with the newer programs ;P

So it worked here...  Please write back if it works for you too...

Terry

PS - The following link is way useful too!!  Probably want to load up all the NTFS tools....  Some (if not all) problems may have been caused since the Seagate FreeAgent drives are formated from the factory with ntfs...  That may have messed up the initial failed mount and corrupted the mount information...  The software should know that the mount is corrupted or failing and retry fresh next time rather than just sitting dead...

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

ANOTHER UPDATE:  I tried it all again and could not get it to reappear unless I ran 

> pmount /dev/sdb1 usbdrive1

As the current user and NOT the sudo user.  Seems if sudo mounts the drive only sudo has access to it...

---

### Post by tapash on 2007-06-21
I have my 120 gb external hard drive. when installed ubuntu 7.04 it was working fine. but after installing write access through the automatix drive just disappeared from the desktop. I tried what you mentioned above installing gnome partition editor it shows in the gnome editor but

sudo pmount /dev/sdb1 usbdrive1

doesn't work.
says command not found

please give reply soon because ihave everything on that i cant use anything. please

---

### Post by drew boardman on 2007-06-21
Dear Terrelf

Thanks for the response, but Gparted won't see the drive either.

Drew

---

### Post by terrellf on 2007-06-23
> sudo pmount /dev/sdb1 usbdrive1
doesn't work.
says command not found

You might try:

> sudo mount /dev/sdb1 usbdrive1

or,

> mount /dev/sdb1 usbdrive1

or,

> pmount /dev/sdb1 usbdrive1

It should have/see the pmount command though...  I did have to do the mounting command under my own user name/login or I could not reach it though due to "security"...  You might try it three times...  It seemed to not work for me once for no apparent reason, untill I "tried again"...

Command not found seems odd to me, but I don't know enough to suggest any more...

> Thanks for the response, but Gparted won't see the drive either.
I think you should try a differnt computer or run Ubuntu off a boot CD to see if it can see the drive then,  The drive itself my have a problem.  I did fine the Seagate FreeAgent 320 gig drive I got from Best Buy on sale had a bad USB cable!!  So do a basic check of the hardware.  Gparted seems to pick up anything and so does the "lsusb" command in terminal.  If the drive is not showing there, might be a hardware issue...

Hope this helps...  I don't know a lot about this stuff, but just suggesting what works for me...

Terry

UPDATE:

I have been running hard drive issues for the last two days and have plugged in like five drives...  But after it all, it can plug in the Seagate FreeAgent drive it it does not show on the desk top automatically...  But If I do (from Application>Accessories>Terminal):

> pmount /dev/sdb1 usbdrive1

It comes up just fine.

It is a software issue here where the main Ubuntu desktop application is frail.  It cannot detect and recover from a bad USB  "initial" detection/installation problem.  It recognizes the drive, but then it "dies" since the first installation and it bad files went bad...  No way to "reset" it to recognize it again to fix the problem...  I tried some things in Windows XP and Windows did detect the problem and recovered just as it should...

IMHO, Ubuntu should detect a new USB drive and try to load it from past information.  Then it needs to "verify" and "insure" that all went well.  If not, it needs to regress and even totally start from scratch or "force" the drive to the desktop.  Plugging a simple USB drive in is a stupid thing and it "should always work"...  Without fail...  If the drive is dead or the data from it is bogus, give an "error message"... 

It is a "weak software" issue...

Terry

---

### Post by drew boardman on 2007-06-29
Sorry for the delay in re-posting.

The issue is now solved.  As i mentioned earlier gparted would not see the drive so I re-installed windows on an old pc , used Partition Magic 8, totally nuked the drive and now its visible again under Ubuntu.

Thanks for all the advice and comments.

Drew

---

