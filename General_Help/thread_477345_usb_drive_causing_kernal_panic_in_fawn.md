---
title: "usb drive causing kernal panic in fawn"
date: 2007-06-18
forum: General Help
---

### Post by collingwoodjoe on 2007-06-18
Hi all, new to forum, I have run into some trouble with my installation of Fiesty Fawn.  install went fine, system running well, but then I put in a usb flash drive and while it showed up in 'places' I couldn't open it, so I removed it and shut down.  

on restart i get an error message that says 
invalid compressed format (err=2) 

then on the next line; 

Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I get the same error if I try to run the liveCD, so whatever it is it is pretty fundemental, however it doesn't seem to be hardware because last night I gave up after trying to reinstall grub on the MBR and tinkering with the advanced settings in the BIOS and went to bed, then I got home this afternoon and decided to have another crack, switched it on and it worked fine!?! Anyway being a masochistic type I thought I would try and recreate the error and inserted my usb disk again, same thing has happened and I can't work out what I did if anything last night to fix it!

could someone help please? I am no linux expert so any advice will be much apreciated.

cheers in advance

---

### Post by longlegs on 2007-06-20
Hi ,
it may be that the event that 'fixed' it was the cold start. Note that a restart is not same as a power off restart.

I suggest that you concentrate on why your system can't open the usb drive. Was it formatted  or written to by XP, ie, is it ntfs? If so then you may need to load the program that helps linux see ntfs partitions.

Linux AND windows can see fat32 partitions.

Good luck!
longlegs

---

