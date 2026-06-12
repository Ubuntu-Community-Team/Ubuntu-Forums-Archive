---
title: "DVD Problems in Feisty"
date: 2007-04-27
forum: General Help
---

### Post by milad on 2007-04-27
I am having few problems with my dvdrom in Feisty which I never had in Edgy.
It doesn't recognize half my DVDs!! and sometimes I can't even eject the dvd rom.

Here's my fstab:

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=e917f964-6f07-4fb2-a84f-4ef038493728 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=b59b70a2-98d5-48ff-bbec-6bcd7380cf0b /home ext3 defaults 0 2
# Entry for /dev/sda2 :
UUID=a4eb39cb-59e6-457e-9901-3a317515090d none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
**/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0**
/dev/hda1 /media/United ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/hdb1 /media/Wind ntfs-3g defaults,locale=en_US.UTF-8 0 0

Does anybody know what's wrong with it?

---

### Post by tictacman on 2007-04-27
It's odd that only some of your dvd's are recognised.  Did you have windows on your machine before ubuntu? Was the drive working ok then?  What sort of dvd's are you trying to read? Movies, data discs etc. Have you tried these discs in another machine to make sure that the discs are not unreadable? I recently had a similar problem and found that the actual dvd drive was faulty (I admit that it was about 3/4 years old).


Also when the dvd-rom is having difficultly reading your discs, for whatever reason, in my experience ubuntu tends to hang onto the discs making it difficult to umount, hence your problem with ejecting.

---

### Post by milad on 2007-04-27
The DVDs are fine. I've tested them with Winodows on my laptop and they even worked fine in Edgy. I'm sure it's a problem in Fiesty. Isn't it odd that I can't even eject the empty dvdrom in Ubuntu?

---

### Post by tictacman on 2007-04-27
If your drive is faulty it will have difficulty recognizing even blank discs.  If your machine can dual boot into windows you could work out whether or not this is the case.  Otherwise perhaps you have a spare pc or maybe a friend who would be willing to test the drive in his machine using windows.  

If thats not an option and you are sure its feisty causing the problem, then perhaps you can try one of the live distros such as knoppix.  I have to say though, that reading from a dvd is a pretty standard out-of-the-box function that doesn't require any manual configuration.

---

### Post by strabes on 2007-04-27
You'll probably have to install libdvdcss2. [http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

---

### Post by goghgoner on 2007-04-27
bump 

I upgraded to feisty and now my DVD drive may not even be under the filesystem window after booting -- sometimes it is, but a movie has never mounted -- when I try to mount (right-click and mount) it errors out saying that it cannot be mounted. I haven't fully tested this but didn't have these problems two days ago with Edgy. I have reinstalled libdvdcss2 and that didn't help.

---

### Post by mdurham on 2007-04-27
Have a look at this bug and add to it if necessary: [https://bugs.launchpad.net/bugs/94119]("https://bugs.launchpad.net/bugs/94119")
My CD/DVD is totally screwed up. It's ok in Edgy though.

---

### Post by goghgoner on 2007-04-28
Thanks for posting the link to the bug report. My cd-rom works fine but my dvd-rom does not mount anything. I'll have to add my files to the bug report. This is my HTPC so the whole mission relies on the DVD drive - ugh. I don't know anything about bug reports so I am wondering about the "medium" importance? 


Here's my fstab: 

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

I don't have a floppy drive installed in my box.  

Here's from dmesg:
[   21.336409] hda: SONY CD-RW CRX230ED, ATAPI CD/DVD-ROM drive
[   22.123107] hdb: DVD-ROM BDV316G, ATAPI CD/DVD-ROM drive

---

### Post by mdurham on 2007-04-28
In my case I'm 99.9% sure that the problem is the driver not working with my LG DVD
I installed an old CD only, and it worked 100%. I hope a fix happens soon.

---

### Post by milad on 2007-05-01
Well, I am using a LG DVD-ROM too so i guess that may be the case.

---

### Post by DagMan on 2007-05-01
What happens if you  manually mount them and and see if anything appears at the mount point?

---

### Post by Chriss.Hi on 2007-05-05
same here with LG-DVD
It happens only sometimes...
eject -v /media/cdrom0 says, that cdrom0 is not mounted and was successful ejected, which is not the case!
Anyone else with that problem (or who fixed it) ?

---

