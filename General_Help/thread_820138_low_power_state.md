---
title: "low power state?"
date: 2008-06-06
forum: General Help
---

### Post by LordVeovis on 2008-06-06
Ok, what brought me here was the hope that there may be some way to leave a computer "running" as in active programs (such as streaming media from online) and have the system run from ram so one could shut the hard drives down?

Incase there is a better way to do what i want, what i do is listen to music when I go to bed, but my PC is loud because I have to have high speed fans to cool my hdds.  I would like a way to not need the HDDs and therefore the fans.  Prefferebly with out requiring a reboot or disconecting any hardware.

I currently have the OS installed on an 8 drive aray made of 15k rpm scsi drives.  I also have 3 sata hdds, and 1 ide hdd and Nvidia sli.  My pc puts off alot of heat and cost ALOT of money to leave running all night because of that.  Fans are on a rpm control and on / off switch.

I want to be able to listen to music online at night w/o having to have hdds running.

*Edited for clarity*

---

### Post by sdennie on 2008-06-06
It's possible to keep your drives in standby most of the time using scripts.  For this specific case, it may be easiest to use laptop-mode though.  You can use that to set your disks to only spinup about once every mp3 fairly easily.  You'll have to google for how to do that though because, I've never set it up in that manner.

Edit:
This may not be a great idea though because desktop disks generally only have a limited number of spinup/down cycles before it can start to cause problems.  I would thoroughly read about both how to do this and what the risks are before trying it.

---

### Post by cariboo on 2008-06-06
xmms has an alarm clock function that works basically the same way a clock radio works. Unfortunately the folks at Debian have seen fit to discontinue it in the repositories. So it looks like you'll have to find it elsewhere. If you search the forums you can find a link to it.

Jim

---

### Post by LordVeovis on 2008-06-06
> **vor said:**
> It's possible to keep your drives in standby most of the time using scripts.  For this specific case, it may be easiest to use laptop-mode though.  You can use that to set your disks to only spinup about once every mp3 fairly easily.  You'll have to google for how to do that though because, I've never set it up in that manner.

This may help out.  Anothing thing to not though is that I am streaming the media (from a website), so I could litterally turn the HDDs off for most of the night and day as I out at work.  Is there a way to selectively suspend disksthough.  For example, if I did want to listen to media from my computer over night can I have all the raid drives suspend (remember the raid drives have the OS on them) but not the storage drive?  The storage drive in my case is 1 or 2 of the sata drives, depending on what i want.  2 of the sata drives are in a software mirrored raid, the third is not.

Also I assume that if I am able to selectively shut down the disks would that still let me save data to a disk that is not shutdown? For instance, if I would like to download a file over night, would I be able to shut off the hardware raid and leave the software raid active for DL purposes (OS is on hardware raid)

---

### Post by Jebdm on 2008-06-06
If you're not downloading anything, then it seems like an easy hack would be to simply boot from a live CD (configured with the necessary files).

Don't know if that's what you're looking for-- kind of a pain in the *** to do every night-- but it seems like it would work.

---

### Post by sdennie on 2008-06-07
Thinking about this a bit more, if you have plenty of RAM, you could use the laptop-mode method and use readahead to try to get a large playlist into the cache.  This should get you moving in the right direction on how to do that: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

---

### Post by LordVeovis on 2008-06-08
ok, I think I thought of a solution myself, but I don't know enough about linux to be surethis works.  Since I have plenty of storage, I wouldn't mind this, but rebooting is annoying to do every night.

Is it posible to do a copy of all my system related files to my mirrored raid an chroot to it at night w/ a script that will susspend the raid 5 (OS raid)?  Is this possible? I don't know enough about how chroot works, nor the state the PC is in after the chroot...

---

