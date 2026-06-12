---
title: "BIOS is locked - flash and reinstall grub?"
date: 2007-10-16
forum: General Help
---

### Post by cmol on 2007-10-16
Hey Fella's :-)

Bought this pc from an internet cafe half a year ago, and installed winxp pro and ubuntu 6.10...

I just found out that my BIOS i locked with a password.. So i can boot, but i can't change my boot list or anything else in the BOIS..

So i thought..

If i made a backup of my grub, flashed my BOIS, booted up on the live disc, reinstalled the grub, and wrote the backup data to the grub..

Would that solve my problem without erasing all the important data from the BIOS?

And by the way: How would i do that? :P I'm not all new at linux just so you know, but I haven't really worked with this before..

I'm running a Phoenix BIOS


Thanks :-)

---

### Post by Whiffle on 2007-10-16
Have you checked the motherboard for a password or bios reset jumper?

---

### Post by dfreer on 2007-10-16
If you can't find the jumper to reset the BIOS, simply remove the Battery (CMOS battery), turn it on, turn it off, and then reinsert the battery. That should wipe everything in CMOS, leaving you free to modify BIOS settings.

Basically, all user settings (including BIOS password) are saved in a sort of RAM, that only retains information while powered (hence the battery). The BIOS itself is stored in non-volatile memory, and won't be affected by a normal loss of power.

---

### Post by cmol on 2007-10-16
> **Whiffle said:**
> Have you checked the motherboard for a password or bios reset jumper?

No, I haven't.. But if i just reset it, i'll lose oll of my boot options.. I can't even read my BIOS, so it wouldn't be wise to reset it without having any boot data i could write back into it..

---

### Post by dfreer on 2007-10-16
GRUB is not stored in any way in BIOS or CMOS. You are mistakenly confusing it with the MBR, which is stored in the first 512 bytes of the Hard drive. You will not lose any boot options by clearing CMOS.

---

### Post by cmol on 2007-10-16
> **dfreer said:**
> GRUB is not stored in any way in BIOS or CMOS. You are mistakenly confusing it with the MBR, which is stored in the first 512 bytes of the Hard drive. You will not lose any boot options by clearing CMOS.

There are not any boot data stored in the BIOS?

---

### Post by Whiffle on 2007-10-16
> **cmol said:**
> There are not any boot data stored in the BIOS?

Nope!  Its all in the master boot record of the hard drive :)

---

### Post by cmol on 2007-10-16
> **Whiffle said:**
> Nope!  Its all in the master boot record of the hard drive :)

Nice! :)

Now i'm all happy.. Hehe.. But why are there a password option then, if you can just reset it like that? Seems silly..

---

### Post by lynxus on 2007-10-16
It is silly, But it used to keep people from messing up a PC without opening it up. Handy if its in a Internet cafe etc.

Bios will contain stuff like.
- Boot list ( Ie: does it check floppy before the harddrive for an os first )
- memory settings
- other crap thats needed to get your machine up and running ready for an OS to take over.

Once its posted. It will read the MBR on whatever it found an dthen boot form whats listed..IE: your grub stuff..

So as those guys up above said. Remove the battery clear the bios. Plug it back in change any settings ya need in Bios and your machine will boot just like it used to.

---

### Post by benerivo on 2007-10-16
The password option is there for people who don't want the hardware settings altered. For example someone who owns an internet cafe doesn't want people to stick an ubuntu cd in and reboot the computer, so they set the BIOS not to try to boot from the cd drive.

---

### Post by dfreer on 2007-10-16
Nope. Short answer is that it is safe to reset your CMOS, as long as you make sure to change the boot order if needed to boot to the correct hard drive. Long answer below:

All that happens in terms of booting the computer, is that you specify in which order you want BIOS to check bootable devices (CD-ROMS, hard disks, floppies, etc). Once the computer passes the POST, it will check and load the first 512 bytes of whatever medium you specify (obviously, booting off the network is a different technology). It's kind of a blind process, it doesn't care what it boots. Anyways, this first 512 bytes is called the Master Boot Record (MBR), and it is where GRUB will put it's Stage 1 (Windows will always overwrite the MBR with it's own code). This basically just gives some basic instructions on where to find the rest of the bootloader (it isn't all contained in the MBR), GRUB stage 2 (the part where you see a menu, and can choose which OS to actually boot to). This can also be likened to NTLOADER, which windows uses to boot single/multiple windows installations (and can also be used to load linux if done correctly), if you ever installed two windows OS's or reinstalled windows, you may have seen this. Anyways, GRUB stage 2 will directly load the linux kernel of your choice, or in dual-boot enviroments it can pass control to NTLOADER in order to boot windows. Tada!

EDIT: It is sort of silly that is so easy to reset CMOS, but that's why physical access to a machine is ALWAYS a bad idea in terms of security. Any machine can be compromised if the attacker has physical access. Servers generally lock the case with a key, and are stored in cabinets which can be further locked. It's also an idiot deterrent, think of a inquisitive 12 year old who wonders what pressing the <Del> key on bootup will do... :D

---

### Post by cmol on 2007-10-16
> **lynxus said:**
> It is silly, But it used to keep people from messing up a PC without opening it up. Handy if its in a Internet cafe etc.

Bios will contain stuff like.
- Boot list ( Ie: does it check floppy before the harddrive for an os first )
- memory settings
- other crap thats needed to get your machine up and running ready for an OS to take over.

Once its posted. It will read the MBR on whatever it found an dthen boot form whats listed..IE: your grub stuff..

So as those guys up above said. Remove the battery clear the bios. Plug it back in change any settings ya need in Bios and your machine will boot just like it used to.

And the bios do not contain any info on where the MBR is placed? IE: If the first 512 bytes of the drive were corrupted, and the MBR was placed after that..

(And the internet cafe i bought this from apparently didn't see that coming.. The machine boots: CD, floppy(?), Hard drive, network :P)

---

### Post by lynxus on 2007-10-16
Humm, you mention the MBR part being corrupt... I wouldnt know sorry.

As far as i know the system will just check there by default. the BIOS doesnt control or store any of that data, thats on the harddrive. However if the harddrive itself has a corrupt MBR then i wouldnt like to guess what would happen.

All the BIOS does it get your system up and ready for something better to happen hehe, IE: an OS taking ownership. ( BIOS - Basic Input Output System ) Enough for IO to happen.


I Suppose if your MBR was fekkered, you could still boot from CD and fix it somehow from a live CD

---

### Post by cmol on 2007-10-16
> **lynxus said:**
> Humm, you mention the MBR part being corrupt... I wouldnt know sorry.

As far as i know the system will just check there by default. the BIOS doesnt control or store any of that data, thats on the harddrive. However if the harddrive itself has a corrupt MBR then i wouldnt like to guess what would happen.

I don't know if the MBR is corrupt.. It boots fine now.. But if all the data i stored on the hard drive, why is the BIOS password not?

(Yes i know.. All these dumb questions :P)

---

### Post by lynxus on 2007-10-16
the BIOS password is stored in Cmos i think? Not sure cant remember.

But as the other guys said. If your PC boots ok now, then removing teh battery and clearing the BIOS password ( So it has no password and the BIOS is back to Default settings ) your machine will be fine.

If you get odd issues after, just go into the BIOS and play with settings.

---

### Post by cmol on 2007-10-16
> **dfreer said:**
> Nope. Short answer is that it is safe to reset your CMOS, as long as you make sure to change the boot order if needed to boot to the correct hard drive. Long answer below:

All that happens in terms of booting the computer, is that you specify in which order you want BIOS to check bootable devices (CD-ROMS, hard disks, floppies, etc). Once the computer passes the POST, it will check and load the first 512 bytes of whatever medium you specify (obviously, booting off the network is a different technology). It's kind of a blind process, it doesn't care what it boots. Anyways, this first 512 bytes is called the Master Boot Record (MBR), and it is where GRUB will put it's Stage 1 (Windows will always overwrite the MBR with it's own code). This basically just gives some basic instructions on where to find the rest of the bootloader (it isn't all contained in the MBR), GRUB stage 2 (the part where you see a menu, and can choose which OS to actually boot to). This can also be likened to NTLOADER, which windows uses to boot single/multiple windows installations (and can also be used to load linux if done correctly), if you ever installed two windows OS's or reinstalled windows, you may have seen this. Anyways, GRUB stage 2 will directly load the linux kernel of your choice, or in dual-boot enviroments it can pass control to NTLOADER in order to boot windows. Tada!

EDIT: It is sort of silly that is so easy to reset CMOS, but that's why physical access to a machine is ALWAYS a bad idea in terms of security. Any machine can be compromised if the attacker has physical access. Servers generally lock the case with a key, and are stored in cabinets which can be further locked. It's also an idiot deterrent, think of a inquisitive 12 year old who wonders what pressing the <Del> key on bootup will do... :D

Nice.. Just what i needed to hear (the long story ;))..
When people just says: "I think it'll work", i don't get to pleased about messing with my BOIS.. The technical explernation is the thing you can trust :) Thanks..

To Lynxus to :)

I'll post how it goes tomorrow when i try.. For now, I will head to bed (it's 11:26 PM  here in denmark)..

Thanks Again :-)

---

### Post by cmol on 2007-10-18
> **cmol said:**
> Nice.. Just what i needed to hear (the long story ;))..
When people just says: "I think it'll work", i don't get to pleased about messing with my BOIS.. The technical explernation is the thing you can trust :) Thanks..

To Lynxus to :)

I'll post how it goes tomorrow when i try.. For now, I will head to bed (it's 11:26 PM  here in denmark)..

Thanks Again :-)

Wuhu.. It worked..

Thanks for the support :)

---

### Post by dfreer on 2007-10-18
Glad to help!

---

