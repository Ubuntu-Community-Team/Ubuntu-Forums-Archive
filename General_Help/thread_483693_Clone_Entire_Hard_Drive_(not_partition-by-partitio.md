---
title: "Clone Entire Hard Drive (not partition-by-partition)"
date: 2007-06-25
forum: General Help
---

### Post by SNYP40A1 on 2007-06-25
My sister messed up her Dell Windows XP laptop installation sometime earlier this year and after about a month of bad experience with Dell tech support, they eventually sent her a new hard drive with the factory stuff pre-installed.  So because I was not around to help, she installed the hard drive that they sent her and started using that.  So now she is happy with the current configuration except for one problem.  The hard drive that was sent to her is smaller than the hard drive which got corrupted.  So I would like to clone the small hard drive bit-by-bit to the new hard drive and then use something like GParted to consume the unallocated excess space onto the main partition.  The problem is that Dell adopts the wasteful strategy of allocating extra partitions for their bloated WinXP installation.  So there is the main partition which is the only partition that really ever gets used, plus there is a install partition that takes up about 3-4 GB of space that contains the installation.  Plus there is another partition for something else, not sure what...  If this was a PC hard drive, I would hook up the two hard drives in one PC and use Drive Clone to transfer the data.  But since this is a laptop (and I only have one LAPTOP to PC IDE adapater), I think I need to actually clone an image of the entire drive to my larger hard drive that Linux is installed on, and then copy the image onto the laptop drive.  So it would look something like this:

Laptop Drive (small) -> PC HD (Linux)
PC HD (Linux) -> Laptop Drive (large)

So can I do that and copy all partitions at once by creating a drive image?  Any idea how?

---

### Post by DagMan on 2007-06-25
You want to run a live cd and use a program called dd
[http://ubuntuforums.org/showthread.php?p=2897470](http://ubuntuforums.org/showthread.php?p=2897470)
That was just a quick search so if the thread isn't helpfull, search more along those lines.
I haven't used this but it's a well respected way to go about it.  There's also a program that will do compression with it called partimage but I don't know if it will backup the entire drive and boot sector as you're wanting.

---

### Post by ukripper on 2007-06-28
> **SNYP40A1 said:**
> My sister messed up her Dell Windows XP laptop installation sometime earlier this year and after about a month of bad experience with Dell tech support, they eventually sent her a new hard drive with the factory stuff pre-installed.  So because I was not around to help, she installed the hard drive that they sent her and started using that.  So now she is happy with the current configuration except for one problem.  The hard drive that was sent to her is smaller than the hard drive which got corrupted.  So I would like to clone the small hard drive bit-by-bit to the new hard drive and then use something like GParted to consume the unallocated excess space onto the main partition.  The problem is that Dell adopts the wasteful strategy of allocating extra partitions for their bloated WinXP installation.  So there is the main partition which is the only partition that really ever gets used, plus there is a install partition that takes up about 3-4 GB of space that contains the installation.  Plus there is another partition for something else, not sure what...  If this was a PC hard drive, I would hook up the two hard drives in one PC and use Drive Clone to transfer the data.  But since this is a laptop (and I only have one LAPTOP to PC IDE adapater), I think I need to actually clone an image of the entire drive to my larger hard drive that Linux is installed on, and then copy the image onto the laptop drive.  So it would look something like this:

Laptop Drive (small) -> PC HD (Linux)
PC HD (Linux) -> Laptop Drive (large)

So can I do that and copy all partitions at once by creating a drive image?  Any idea how?




Try clonezilla,
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by SNYP40A1 on 2007-07-02
Yup, I think Clonezilla is what I want.  I will try it later tonight.

---

### Post by rrinker on 2007-07-02
Not sure about which Open-Source software will do this, but at work I use Ghost a lot and it will definitely do this. In fact I used Ghost on this old Optiplex 260 to switch from the stock 20GB drive to an 80GB drive after I installed Fiesty on it. I've done plenty of upgrade drives with Windows on them this way, simple select the source partition and then select the new drive, the default in Ghost will fill the new drive rather than create a partition of the same size as the source.

                                                           --Randy

---

### Post by ukripper on 2007-07-03
> **rrinker said:**
> Not sure about which Open-Source software will do this, but at work I use Ghost a lot and it will definitely do this. In fact I used Ghost on this old Optiplex 260 to switch from the stock 20GB drive to an 80GB drive after I installed Fiesty on it. I've done plenty of upgrade drives with Windows on them this way, simple select the source partition and then select the new drive, the default in Ghost will fill the new drive rather than create a partition of the same size as the source.

                                                           --Randy

Don't underestimate open source. Try Clonezilla it is far ahead of Ghost.

For more information visit clonezilla website.

---

### Post by rrinker on 2007-07-03
Oh I'm not underestimating anything, I'm just not familiar with any of the open source equivalents to Ghost, just know that Ghost can do what the OP wanted.

                                           --Randy

---

### Post by Shazaam on 2007-07-03
Before you do anything, search google for "Dell De-Crapifyer" and use it. Then go to "Disk Cleanup" and run it. Reboot into 'Safe Mode" and deframent the hard drive. Reboot into normal mode.
Once you are done then clone it. I hear clonezilla is good. When you are done cloning let Windows do a checkdisk at boot (automatic) and you should be good to go.

---

### Post by LaRoza on 2007-07-03
> **rrinker said:**
> Oh I'm not underestimating anything, I'm just not familiar with any of the open source equivalents to Ghost, just know that Ghost can do what the OP wanted.

                                           --Randy

There is also a "Ghost for Linux".

---

### Post by az on 2007-07-03
Don't forget about dd

sudo dd if=/dev/hda of=/media/usb/file

---

### Post by l-fever on 2007-07-23
Tested clonezilla today. backed up my entire 160g laptop hard drive to an external 400g usb drive. Worked like a charm! Tested the backup by doing a full restore. I was surprised at how fast the backup/resore runs! :)

---

### Post by SNYP40A1 on 2007-08-12
I am disappointed with Clonezilla.  I am trying to backup an image on an NTFS drive to another NTFS drive using no compression.  I am getting a transfer rate of about 1-2 GB per hour.  At this rate, it will take me a day or two just to create an image, assuming that everything else goes ok.  This is on a P4 3.2 GHz PC with 1 Gig ram.

---

### Post by ukripper on 2007-08-13
> **SNYP40A1 said:**
> I am disappointed with Clonezilla.  I am trying to backup an image on an NTFS drive to another NTFS drive using no compression.  I am getting a transfer rate of about 1-2 GB per hour.  At this rate, it will take me a day or two just to create an image, assuming that everything else goes ok.  This is on a P4 3.2 GHz PC with 1 Gig ram.

Try backing up on another media, USB or other HDD

---

### Post by wirelessmonkey on 2007-08-13
I use partimage, it's fast, easy, has command-line or curses interface.... Faster than clonezilla for my needs.

---

### Post by SNYP40A1 on 2007-08-13
Yeah, I tried Partimagic and it seems to work better.  Unfortunatually, after copying the hard drive and inserting the new HD into the laptop, it booted half way through Windows then just froze.  So I think there was a copy error someplace.  Anyone know of a good free program to check hard disk integrity?  Maybe the hard drive is damaged.

---

### Post by ukripper on 2007-08-14
> **SNYP40A1 said:**
> Yeah, I tried Partimagic and it seems to work better.  Unfortunatually, after copying the hard drive and inserting the new HD into the laptop, it booted half way through Windows then just froze.  So I think there was a copy error someplace.  Anyone know of a good free program to check hard disk integrity?  Maybe the hard drive is damaged.

use ubuntu Live CD  and run fsck -v for integrity check

---

### Post by psusi on 2007-08-14
fsck checks the filesystem, not the media, and it does not understand ntfs.  

If you want to check the media, run badblocks or smartctl from the smartmontools package.

---

### Post by ukripper on 2007-08-15
You can use badblocks as suggested and then to make sure HDD won't use bad sectors use mkfs [http://linux.die.net/man/8/mkfs](http://linux.die.net/man/8/mkfs)

# mkfs -ct <filesystem> <partition device file>

If you want to check integrity of filesystem use fsck


EDIT:
 I would use vendor's supplied diagnostic tool/utility to do the check on media for any bad sectors. If you go to manufacturer's website you will find a diagnostic tool for sure then try that first.

---

