---
title: "Cannot read DVD Media but CDs work fine with the same drive."
date: 2007-05-07
forum: General Help
---

### Post by ALIENDUDE5300 on 2007-05-07
I own an ALIENWARE Area-51 5300 Computer with a Lite-On SOHC-5232K Combo Drive (52x32x52x for CD Media) and DVD-ROM Media. When I Insert ANY TYPE OF DVD MEDIA (Movie, Commercial, Homeburn) into the drive and goto places-computer-cdrw/dvdrom drive, I get a "Unable to mount media. There is probably no media in the drive." This has nothing to do with the media itself because it works when I insert it into another computer (that I don't own, but have access to). I am unsure if it is a problem with the actual drive or if it has to do with Ubuntu's compatibility. The drive DID read DVDs while I was still using windows and it simply doesn't work anymore. This is on a fresh install of Ubuntu 7.04 Feisty Fawn (Installed from Alternative CD). I don't think it is the configuration of the system itself because I recently upgraded it... then again just to be on the safe side... I recently upgraded from 256mb of DDR2 PC3200 ram to 2GB of DDR2 PC4000 ram and installed an ati radeon x1900 graphics card but I highly doubt that has anything to do with it whatsoever. If anyone has any information that can help me I will be forever grateful. I really need this drive to work! I've only had the system for 3 years! [-o<

EDIT: The drive is using the "CO52NK0J" firmware, which is currently the latest version available as of 5/10/07.

---

### Post by mdurham on 2007-05-07
There are many problems and complaints about CD/DVD's see this thread wich is one of many.
[http://ubuntuforums.org/showthread.php?p=2597013#post2597013]("http://ubuntuforums.org/showthread.php?p=2597013#post2597013")

---

### Post by ALIENDUDE5300 on 2007-05-07
That post ended up being completely useless to me :( If you know anything at all that might be useful please post it here.

---

### Post by ALIENDUDE5300 on 2007-05-07
In case it will help identify the problem, here is my lshw output for the cdrom section only because providing the whole thing is unnecessary:
```
           *-cdrom
                description: DVD reader
                product: COMBO SOHC-5232K
                vendor: LITE-ON
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: NK0G
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
```

Here is my /etc/fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a0ecd5cd-6b80-47cf-8e34-632b388128b2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4894E07E94E0703C /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=4529a4ff-14d4-4660-b940-0bcd4b0d3a96 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

A mount command I have tried is "mount /dev/dvd /media/dvd -t udf,iso9660" and the same thing with auto file system type.

EDIT: If you think you can help me I can provide any info you need. I just want to get this problem fixed!

---

### Post by Subban on 2007-05-07
If you had recently been installing new hardware into the box, have you double checked the drives connections, pop them off, give them a blow and reseat them firmly. Worth a try given you have recently been poking around there ;)

If not, don't rule out the drive failing, just a couple of weeks ago I had the exact symptoms you described and it was the dvd drive failing, it would read cd/cdr just fine, but dvd/dvdr/dvdrw went unseen by it, popped in another drive and all was golden once more.

---

### Post by Pikey Joe on 2007-05-07
Combo drive?

I suspect that's the problem - mine wouldn't work either.

---

### Post by ALIENDUDE5300 on 2007-05-07
> **Subban said:**
> If you had recently been installing new hardware into the box, have you double checked the drives connections, pop them off, give them a blow and reseat them firmly. Worth a try given you have recently been poking around there ;)

If not, don't rule out the drive failing, just a couple of weeks ago I had the exact symptoms you described and it was the dvd drive failing, it would read cd/cdr just fine, but dvd/dvdr/dvdrw went unseen by it, popped in another drive and all was golden once more.

I checked all the cables and everything is connected properly, I think that it has something to do with the linux kernel. Besides, replacing the drive is a waste of money if I can possibly find a solution on the forums.

---

### Post by ALIENDUDE5300 on 2007-05-07
> **Pikey Joe said:**
> Combo drive?

I suspect that's the problem - mine wouldn't work either.

I see... if I find a solution I'll let you know ;)

---

### Post by ALIENDUDE5300 on 2007-05-07
bump -- still not working!... It's been 50 minutes since the last post! Can't anyone find a solution?

---

### Post by rbmorse on 2007-05-07
Replace the drive. It's toast.

---

### Post by Subban on 2007-05-08
> **ALIENDUDE5300 said:**
> I checked all the cables and everything is connected properly, I think that it has something to do with the linux kernel. Besides, replacing the drive is a waste of money if I can possibly find a solution on the forums.

Then its almost certainly the drive thats borked. It really does look to be the most likely factor from what you have shown and described, it will also be the fast (if you have one handy) to replace and test.

---

### Post by gelatinouscube on 2007-05-09
I had the same problem with my Plextor. My problem was fixed my changing the file system type in the fstab from udf,iso9660 to auto. I don't believe a comma delimited fstype is allowed, not from what I can tell from man fstab anyway.

Good luck.

- gel

P.S.- All you people out there telling this person to get a new drive before understanding what is going are really doing the Ubuntu community a disservice. Sometimes it's just better to keep quiet.

---

### Post by rbmorse on 2007-05-09
And sometimes it really is the drive that defective.

---

### Post by d80tb7 on 2007-05-10
Well it might be the drive but I have the same problem here (with two different drives both of which work fine in Windows).

I've modified fstab in every way possible nad even tried mounting from the command line but nothing works.  Cd's, on the other hand, automount flawlessley.  This is on x64 if that helps.

In the course of my travels I've found a few other people who appear to have the same problem.  no solution though....

[http://ubuntudaily.com/2007/04/15/my-feisty-regressions-what-are-yours/](http://ubuntudaily.com/2007/04/15/my-feisty-regressions-what-are-yours/)
[http://ubuntuforums.org/showthread.php?p=2579148](http://ubuntuforums.org/showthread.php?p=2579148) (me that started the thread but at least one other person had the same problem)
[http://ubuntuforums.org/showthread.php?t=427258&highlight=can%27t+mount+dvd](http://ubuntuforums.org/showthread.php?t=427258&highlight=can%27t+mount+dvd)
[http://ubuntuforums.org/showthread.php?t=431728&highlight=can%27t+mount+dv](http://ubuntuforums.org/showthread.php?t=431728&highlight=can%27t+mount+dv)

Apart from this Feisty is great...

---

### Post by ALIENDUDE5300 on 2007-05-10
> **gelatinouscube said:**
> I had the same problem with my Plextor. My problem was fixed my changing the file system type in the fstab from udf,iso9660 to auto. I don't believe a comma delimited fstype is allowed, not from what I can tell from man fstab anyway.

Good luck.

- gel

P.S.- All you people out there telling this person to get a new drive before understanding what is going are really doing the Ubuntu community a disservice. Sometimes it's just better to keep quiet.

Thanks for the advice... I'll try that out!

---

### Post by ALIENDUDE5300 on 2007-05-10
> **d80tb7 said:**
> Well it might be the drive but I have the same problem here (with two different drives both of which work fine in Windows).

I've modified fstab in every way possible nad even tried mounting from the command line but nothing works.  Cd's, on the other hand, automount flawlessley.  This is on x64 if that helps.

In the course of my travels I've found a few other people who appear to have the same problem.  no solution though....

[http://ubuntudaily.com/2007/04/15/my-feisty-regressions-what-are-yours/](http://ubuntudaily.com/2007/04/15/my-feisty-regressions-what-are-yours/)
[http://ubuntuforums.org/showthread.php?p=2579148](http://ubuntuforums.org/showthread.php?p=2579148) (me that started the thread but at least one other person had the same problem)
[http://ubuntuforums.org/showthread.php?t=427258&highlight=can%27t+mount+dvd](http://ubuntuforums.org/showthread.php?t=427258&highlight=can%27t+mount+dvd)
[http://ubuntuforums.org/showthread.php?t=431728&highlight=can%27t+mount+dv](http://ubuntuforums.org/showthread.php?t=431728&highlight=can%27t+mount+dv)

Apart from this Feisty is great...

Thanks for the links -- maybe a solution will be found on one of the threads that will work for all of us. ;)

---

### Post by ALIENDUDE5300 on 2007-05-10
> **ALIENDUDE5300 said:**
> Thanks for the advice... I'll try that out!

Nope... it doesn't work still. Although I doubt it is the drive, I have contacted Lite-On IT and described the problem. I still have not received a reply but I contacted them rather recently and I doubt anyone can reply that fast. It's probably best to just be patient now...

---

### Post by d80tb7 on 2007-05-11
Ok I've fixed mine (at the expense of now no longer being able to automount optical media)
In preferences -> removable drives and media I unchecked the following boxes.

1.  'Mount removable media when inserted'
2.  'Browse removable media when inserted'

Now I can mount dvds from the command line with:
mount /dev/hdd /mnt/cdrom/

hope that helps

Chris

---

### Post by rggavubt on 2007-05-14
I'm having the same problem since I upgraded to Feisty.  I can't mount or play DVD's but music CD plays fine in DVD or CD drive.  I think it is a feisty bug???  In Dapper, I could play DVD's fine!

---

### Post by Verminoz on 2007-05-14
OK, maybe I'm wrong but I have reasons to believe what's to blame! I have the same problem in Kubuntu 7.04! Before I installed them on my computer I backed up my data in DVDs and formated my disk. I installed Kubuntu 7.04 and after that I copied **most** of my data from the DVDs back on the hard disk. Everything was fine for a month until the day before yesterday when I inserted one of my backup DVDs to find some uncopied data and I noticed that none of those dvds can be mounted and manual mounting does not work either. It just spits out the same errors yours did.
Some days ago I made some updates the automatic update program found. One of them was the "hal" package which is the Hardware Abstraction Layer and the "libhal" package. All these can be found on my dpkg logs.

So, could it be something about that? It seems rather important and related to hardware devices. Could it be a "hal" bug???

I'm sorry if I'm totally mistaken. I am simply trying to help.

---

### Post by Köntzä on 2007-11-30
Hi,

I had the same problem and last night's Googling suggested that HAL's the culprit. I dunno 'bout that...

Later last night I managed to get DVDs readable again. After Gutsy update, DVD reading stopped working; I could read CDs, and burn CDs AND DVDs, but reading DVDs brought up a bunch of errors.

My HW setup was this:
Hard disks /dev/sda and sdb were hooked up to the IDE cable 1, and DVD-RW (/dev/scd0) together with the third HD (/dev/sdc) to the IDE cable 2. 

Since the third HD was in the system only for Gentoo/Arch testing, and its size was measly 10 GB, I decided to remove it from the system just in case that HD might cause the problem. I don't know enough about the subsystems related to IDE cabling, both HW and SW, but removing the third HD (the one that was attached to the same cable as the DVD-RW was) gave me back DVD reading capability.

Slaínte,
--
Köntzä

---

### Post by TripWire7 on 2007-12-02
This worked for me [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I hope this helps.... after all I'm new here.

---

### Post by TripWire7 on 2007-12-05
Oh I forgot.... I also had to run this command

sudo /usr/share/doc/libdvdread3/install-css.sh

I got that command from here [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd)

after that hopefully you have all the codecs and stuff you need

---

