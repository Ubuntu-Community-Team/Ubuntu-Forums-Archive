---
title: "Dying HDA! How to backup"
date: 2008-05-01
forum: General Help
---

### Post by The-Russ on 2008-05-01
What's up everyone,

I'm hoping somebody can help me find an easy method of backing up my hard drive. Right now I have 2 PATA hard drives in my desktop PC. The primary hard drive is an 80GB which hosts my Windows XP partition and, of course, my MBR.

My secondary hard drive is a 500GB which is currently divided into 4 partitions: 100GB Ubuntu Linux, 100GB Fedora 8, 100GB OpenSUSE, 100GB unused ext3 partition and 100GB of unallocated space.

My primary hard drive is starting to fail and I'd like to make a complete backup of the entire disk in order to transfer it to my new 80GB hard drive that's waiting to be installed. Windows doesn't come with a tool (that I know of) capable of doing this exactly as I'd like it to, and I can't afford to purchase something like Norton Ghost. I use the Ubuntu boot loader, if that information is pertinent.

So my question is: Is there a way for me to backup my primary hard drive through Ubuntu, remove the hard drive, install the new one, and then restore my backup to the new one?

I appreciate any help. Unfortunately I've been spending most of my time at school studying computer hardware and networking, so I haven't had the chance to learn as much about Linux as I'd like, despite being a Linux user for almost a year. But some day, I'll give back to this community, as it's given so much to me already!

---

### Post by hardyn on 2008-05-01
I have never been a back-up-the-disk kinda guy, but i am sure there is.

Im sure you have a good reason, but why not just back up your data (including things like xorg.conf s grub lilo etc), and reinstall the OSs from disk?

---

### Post by The-Russ on 2008-05-01
I was able to do that when I reinstalled Linux a month or two ago. Unfortunately the Windows XP on this machine is a Compaq-specific version, for which I don't have the installation CDs, and the system restoration CDs require that you first boot with a floppy disk, which was terrible planning on behalf of the manufacturer, as this computer didn't come with a floppy disk drive haha.

---

### Post by argosreality on 2008-05-01
You can copy the disk using dd though its extremely slow. Most of the documents I've found dealt with doing under Solaris (where I first learned about it) but the principle is the same. 

```
# dd if=/dev/rdsk/cXtXdXs2 of=/dev/rdsk/cYtYdYs2 bs=blocksize
```

except in this case it would be /dev/hda and /dev/hdb

This must be done on unmounted filesystems as well. Things would get royally screwed up if you do it when datas getting moved around.

[This whitepaper]("http://www.sentinelsecurity.net/whitepapers/diskcloning.pdf") is a decent coverage of it in the linux world and breaks it down per partition at the end as well

---

### Post by hardyn on 2008-05-02
compaq specific? how?  OEMS usually bundle the drivers, but i cant see it being any different than that.

If you find a windows CD that matches the release of windows that you have, the serial should work.  eg: if your machine was licencened with an XP SP2 OEM... then another XP SP2 OEM disk, compaq or not, should work with your licence key... I have done this many times with sucess.

---

### Post by ghost_ryder35 on 2008-05-02
> **argosreality said:**
> You can copy the disk using dd though its extremely slow. Most of the documents I've found dealt with doing under Solaris (where I first learned about it) but the principle is the same. 

```
# dd if=/dev/rdsk/cXtXdXs2 of=/dev/rdsk/cYtYdYs2 bs=blocksize
```except in this case it would be /dev/hda and /dev/hdb

This must be done on unmounted filesystems as well. Things would get royally screwed up if you do it when datas getting moved around.

[This whitepaper]("http://www.sentinelsecurity.net/whitepapers/diskcloning.pdf") is a decent coverage of it in the linux world and breaks it down per partition at the end as well
here is another solution for you on top of using dd
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by confused57 on 2008-05-18
You might also want to look into clonezilla:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

Another link for backing up and restoring:
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
especially the section on backing up the mbr, although an Ubuntu live cd is capable of reinstalling grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Herman is the developer of the hermanzone website and can probably give you more specific advice on how to go about "cloning" your drive.

Good Luck...

---

### Post by The-Russ on 2008-05-19
Whattup everyone,

thank you for all your replies. I tried a few of the suggestions that you guys offered, although I must admit that I'm much more hardware savvy than I am software- especially with using the BASH Shell. I ended up locating a freeware utility for Windows, which did the job and I backed up my hard drive to my second hard drive.

But I've decided it would probably be easier to just go ahead and backup to my single 500GB hard drive on a separate partition (I have ample room). I switched the places of my hard drives within my tower, making my 500GB hard drive with my 3 Linux distros my primary master, and the Windows XP 80GB drive is the primary slave. For some reason, I'm unable to get my boot menu to point correctly to Windows so I can run the backup utility (I'm hoping to do so without switching the hard drives physically again).

In menu.lst, my Windows entry is as follows:

title		Microsoft Windows XP Home Edition
rootnoverify	(hd1,1)
chainloader	+1

When I try booting into it, I get a message that says "Starting up" like it usually does when loading Linux, and then it just sits forever. I noticed that the comment in the file says:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

and my Windows disk is listed (under fdisk) as sdb1 now- not sda2. Is there a way I can make it point to the correct place? I thought I had done everything correctly. Thank you everyone for your help. I truly appreciate it and will some day have learned enough to give back to this community!

---

### Post by confused57 on 2008-05-19
You could try adding map lines to your Windows entry:
```
title Microsoft Windows XP Home Edition
rootnoverify (hd1,1)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by The-Russ on 2008-05-19
That worked perfectly! Thank you so much for your help!

---

### Post by |{urse on 2008-05-19
You will find that the windows coa (activation key) will work with any windows xp disk. If you have to call to activate inform the person on the phone that you are an oem systembuilder reinstalling for a customer. It's on their scripts.

---

### Post by confused57 on 2008-05-20
> **The-Russ said:**
> That worked perfectly! Thank you so much for your help!
Glad it worked and to have helped.  I now know who to consult, if I ever need to backup or clone a hard drive with Windows.

---

