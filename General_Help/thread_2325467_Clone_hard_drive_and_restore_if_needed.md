---
title: "Clone hard drive and restore if needed"
date: 2016-05-22
forum: General Help
---

### Post by blekm2 on 2016-05-22
Hi guys,

I've installed Ubuntu and I've set everything up for work (software engineer). Now that my system and ready for developing purposes I would like to create an EXACT COPY (including all the partitions, /boot, /home, etc etc) of my hard drive and save it to an external hard drive. 

So, if necessary, I can just plug in the hard drive back and restore fully the backup, without having to go through the entire install + setup again..

Any suggestions?

I've done my homework and I've seen Clonezilla and dd (not sure both of them do what I exactly want) but I would like some personal opinions too, please :D

---

### Post by monkeybrain20122 on 2016-05-22
I use fsarchiver for exactly that. It is easy to use and has the flexibility that you can restore to a smaller partition than the original one as long as it is big enough for the content (the original may be mostly empty) If you use things like clonzilla you would have to make the target partition bigger than the original or shrink the original first. 

It is fast and you can do live cloning when you are using the computer (use the options -a and -A with the savefs command)

Since it only copy files it is quite flexible, I have successfully copied my system with a gpt harddrive (two primary partitions. / and /home) to a MSDOS one (one primary partition and one logical inside an extended partition in a multiboot external drive)  with no issue. Never worked with /boot partitions though, I always have only / and /home. Also I always turn off uefi but if you have it on you may have to separately make a FAT partition, fsarchiver doesn't do FAT as far as I know.

fsarchiver is in the repo.

Edited: if you clone to an external drive this way you should change the uuid of your partitions in the original (or in the clone if you have access to another computer) afterwards, otherwise you can't boot the clone off the original machine or unmount it after you log into the original system and then plugin the external. The system gets confused about which partition is which. You can google how to do this or post back if you need help.

[URL="https://www.fsarchiver.org/QuickStart"]https://www.fsarchiver.org/QuickStart

[/URL]

---

### Post by blekm2 on 2016-05-22
I have 4 partition (I've installed Ubuntu on XPS 13 that had Windows 10 originally). So I've formatted the drive and created like this

/dev/nvme0n1
--/dev/nvme0n1p1 ext4 /boot
--/dev/nvme0n1p2 swap
--/dev/nvme0n1p3 ext4 /
( I think I have another one for /home, but I can't recall now)

That's what I had to do to make it work correctly. I would like a clone that copies the extra drive, as it is! So that I can restore if in fully, if necessary.

---

### Post by atrab101 on 2016-05-23
> ... I've seen Clonezilla... 

I built a new system with dual boot of Windows XP and Ubuntu 14.04 LTS a few months ago.  I have separate hard drives for each.  Everything works remarkably well, and I have had zero problems.  

I have always done disk images for backups in Windows with the Acronis program.  The ability to restore everything has saved me LOTS of trouble and time on a few occasions.  I decided that I would like to do the same for my Ubuntu Drive.  I probably could have backed up the Linux Ext4 drive from Windows using Acronis with a sector-by-sector approach, as my version of Acronis does not support Ext4, but I decided I would rather keep my Windows and Ubuntu drives completely separate (hiding and no mount of drive by other OS).  So I did some research as you did, and I decided on Clonezilla which works perfectly for a complete disk image with all partitions, swap, etc. on Ubuntu drive.  

I burned a DVD of Clonezilla-Live 20160210-Wily-AMD64.  I had initially installed Ubuntu on a used drive with a lot of hours on it, but after two months of use I loved Ubuntu and decided it should have a brand new Western Digital Black Drive.  I figured the proof of Clonezilla would be restoring a disk image with my two months of Linux work and history.  I hate starting over.  I booted from the DVD, and ran Clonezilla.  There are a lot of choices on the menu, but it was easy to figure out the correct selections, in most cases a default.  I saved the image to an external Ext4 formatted drive which is necessary to preserve all file attributes.  I then installed the new drive in place of the used one, booted to the Clonezilla DVD again and restored the image to the new drive. My drive and system restored perfectly and booted with no problem. I now create images weekly or would more often if very big changes or trying risky things.  

I vote for Clonezilla!  I am a complete novice to Linux and was able to use it with no problems.  :D

Regards

---

### Post by sudodus on 2016-05-23
Both Clonezilla and dd can do the job, but I would say that Clonezilla is better for several reasons. It is safer and it is faster. There are 'checkpoint questions'. It only copies used blocks.

Clonezilla cannot restore to a smaller drive, it needs a drive of exactly the same size or larger.

I have used Clonezilla for years to make cloned images of the system partitions. I have a separate ***data*** partition, which I back up separately (and more often). There are several backup or synchronizing tools to backup a data partition.

---

### Post by blekm2 on 2016-05-23
I don't care about the problem of cloning in a smaller drive, I'll be cloning back on the same drive (that's the plan anyway). 

So Clonezilla will copy the exact structure of my hard drive (/boot, /home etc etc) so that I can restore it exactly like that?

Is it bootable from USB? I don't have a CD...

---

### Post by atrab101 on 2016-05-23
It restored entire disk for me perfectly.  It booted with no problem.  You should test it as I did, if possible, if you have another drive to restore to.  Your current drive can be removed when restoring to another so no risk to your data.

The Clonezilla site says USB is fine:  [http://clonezilla.org/liveusb.php](http://clonezilla.org/liveusb.php)  

Regards

---

### Post by sudodus on 2016-05-23
Yes and yes :-)

Download a Clonezilla iso and check the md5sum. I prefer the ***stable*** version of Clonezilla. See [http://www.clonezilla.org/](http://www.clonezilla.org/)

I have Clonezilla both on CD and on USB. I use [mkusb](https://help.ubuntu.com/community/mkusb) to create USB boot drives from iso files.

---

### Post by monkeybrain20122 on 2016-05-23
> I have 4 partition (I've installed Ubuntu on XPS 13 that had Windows 10  originally). So I've formatted the drive and created like this

/dev/nvme0n1
--/dev/nvme0n1p1 ext4 /boot
--/dev/nvme0n1p2 swap
--/dev/nvme0n1p3 ext4 /
( I think I have another one for /home, but I can't recall now)

That's what I had to do to make it work correctly. I would like a clone  that copies the extra drive, as it is! So that I can restore if in  fully, if necessary.                         

Hi, see this long thread (or see the last page first and going back if it is not clear). So the guy said it works for his /boot partition as well. Don't need to clone swap, just make a new one.

You don't need a usb or burn any cd with fsarchiver, clone the files to an external drive (say a storage partition in your drive) using live cloning, then restore it to the appropriate partitions in the external. Since it only copies the file system instead of doing sector by sector it doesn't really care how your external drive is partitioned (whether gpt or MSDOS) as long as different partitions get restored to their designate destinies.I think it is faster than clonezilla as well.

[http://ubuntuforums.org/showthread.php?t=2221842&page=4](http://ubuntuforums.org/showthread.php?t=2221842&page=4)

---

### Post by blekm2 on 2016-05-23
great, thanks guys

---

### Post by sudodus on 2016-05-23
> **atrab101 said:**
> It restored entire disk for me perfectly.  It booted with no problem.  You should test it as I did, if possible, if you have another drive to restore to.  Your current drive can be removed when restoring to another so no risk to your data.

The Clonezilla site says USB is fine:  [http://clonezilla.org/liveusb.php](http://clonezilla.org/liveusb.php)  

Regards

+1

***You should only rely on a backup method that you have tested.*** And to test, you need an extra drive (because you should not take the risk with your original drive).

---

