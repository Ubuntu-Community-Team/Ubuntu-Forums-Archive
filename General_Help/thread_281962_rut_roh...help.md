---
title: "rut roh...help"
date: 2006-10-21
forum: General Help
---

### Post by sin1984 on 2006-10-21
help...i wanna uninstall ubuntu!!

when i restarted my comp, it went to the screen where it asks what OS you want to load. and when i clicked on windows it gave me " INF file txtsetup.sif is corrupt or missing, status 14. setup cannot continue. press any key to exit."

so now i'm sweating bullets in fear that i may have lost my windows.

i created a partition for ubuntu, and thats where my / is at. but i'm lost on how to uninstall ubuntu and get my windows back =(

---

### Post by sin1984 on 2006-10-21
bump

---

### Post by podunk on 2006-10-22
I don't know how to fix the problem - but if you have a good Ubuntu install I don't think you have to worry about losing your Windows data. If worst comes to worst your be able to copy it to a USB drive or DVD

---

### Post by bruenig on 2006-10-22
Uninstalling ubuntu won't solve your windows problems.

---

### Post by sin1984 on 2006-10-22
well thats good to know....but i'd really like a solution as to how to get windows back.

---

### Post by Cynical on 2006-10-22
why does it say setup cannot continue? did you just install windows or something?

---

### Post by skwillz on 2006-10-22
I don't know how well you are with the recovery console on the XP disk, but that's an obvious first choice.

Next option would be to reinstall WinXp on top of the existing partition (as in: don't mess with partitions.. just pick the existing one as the install location) and get your base system running fine again.

This, of course, would probably repair your MBR to windows, so you'd have to use the Ubuntu install CD to reinstall grub.

Good luck.

---

### Post by sin1984 on 2006-10-22
i cant find my recovery CD so i cant use that method to restore my comp. 

no i didnt just install windows either. it is just saying
"INF file txtsetup.sif is corrupt or missing, status 14. setup cannot continue. press any key to exit"

thats why i'm at a loss. i have no idea where to start...without that CD i think i'm screwed.

i wish there was a system restore option to where i could just go back in time like in windows.... i was curious about ubuntu, i heard alot of good stuff.so i thaught i'd try it but i think i'm gonna stick with windows, if i can get it up again...
but this is all i did so far.....and this is where i think i messed up. /media/sda1 is where i had windows. /media/sda2 is recovery and then / is the partition that i tried to make just for ubuntu...

ok, so i partitioned my harddrive and made a 40gb partition for ubuntu. its a ext3 filesystem. when i select it and click forward, i get to the "prepare mount points" screen which it says
select wich partitions you want to use for your new instiallation, and where you want to mount each of them
you must mount one partition on the root file system ("/") and you must choose at least one partition for use as swap space.

below that i have 3 mount point rows in a table and they are as follows: (the -'s are just to show empty space)

mount point-------------partition-----------------------------

/media/sda1--- partition 1 disc, usb/scsi/sata 1 (primary) [sda1]
/media/sda2--- partition 2 disc, usb/scsi/sata 1 (primary) [sda2]
/----------------- partition 3 disc, usb/scsi/sata 1 (primary) [sda3]

with a check box in reformat, in the partition 3 row

---

### Post by podunk on 2006-10-22
There are 5 pages of that error in goggle with zero resolutions (in English any way). A lot of them end up being hard drives going bad. The others seem to involve trying to enter recovery mode with a set up disk different that the one used to set it up.

Unfortunately, no hits at all on MS Knowledge Base or Tech Net.

If your computer didn't come with a Windows XP disk but instead has restore disks the computer company offers those cheap. Like 10 bucks or so, so you won't have to spring 200 for a full install of XP. Restore disks will of course wipe your set up and any data.

Every Windows user gets 2 free support incidents via email &#8211; now might be a good time to use one of them. :-) You'll need the Windows product key (which is usually on the back of the computer for newer machines).

Every hard drive manufacturer has diagnostic utilities on their web site to test the hard drive, you might want to download the one for yours. 

If you have any data that matters (kids pictures, tax returns, passwords etc) I'd suggest using Ubuntu to get them off the computer and onto DVDs or something. See this page on mounting and reading Windows drives in Ubuntu:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

