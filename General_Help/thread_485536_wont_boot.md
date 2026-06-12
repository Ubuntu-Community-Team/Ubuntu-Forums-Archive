---
title: "wont boot"
date: 2007-06-27
forum: General Help
---

### Post by dwm09 on 2007-06-27
well i installed it on a secondary hard drive and when i try to boot up into ubuntu it goes to the loading screen and once its done it takes me to a black screen with a strip of lines going across it. anyone know what it means or anything about it?

---

### Post by charleseddy on 2007-06-27
Despite not having much information on the situation, I'd say A. Faulty hard drive *or* B. Faulty linux install.  However, I could be wrong because I have such a scant amount of info.  I'm assuming that you're talking about the splash screen (the one that says Ubuntu on it with the orange bar going across).  Have you tried, yet, going into failsafe mode when it comes up with the operating system choices, logging in, and typing startx?  Does the splash screen finish loading (the bar gets all the way across)?  Which version of Ubuntu are you using?  When did you install Ubuntu; has it ever worked on your PC, or is this your first try?  If it's not your first try and it's worked before, what was done differently before?  What is your master/slave configuration on the hard drives, and what other operating systems are installed?

These are just a few questions to start the troubleshooting process.  Thanks,

ce

---

### Post by dwm09 on 2007-06-27
well now the problem is that right now im on my moms laptop and my main computer wont boot into anything now. befor bed i remember deleteing the linux partition on my new hard drive (because it wouldnt boot into linux). so then i wake up this morning and start up my computer its says: 
GRUB Loading stage 1.5.
GRUB loading please wait...
Error 22

and i dont know what that means. i tryed starting the computer up with out the new hard drive pluged in and it says the same thing but "Error 21"....and i cant even get to the "HP recovery" partition on my main hard drive.

---

### Post by dwm09 on 2007-06-27
1) yes it finishes loading then goes into the weird screen.
2)ubuntu 7.4
3)i installed it last night, and this is my first time installing ubuntu. i have been useing it on the live cd and it worked like a dream.
4) umm my hard drives are SATA so there is no special config i think.
5) i have windows xp home edition.

---

### Post by charleseddy on 2007-06-27
error 22 usually means it can't find the partition that grub refers to . . . do a search on the forums for reinstalling GRUB and try that.

---

### Post by confused57 on 2007-06-27
> **dwm09 said:**
> 1) yes it finishes loading then goes into the weird screen.
2)ubuntu 7.4
3)i installed it last night, and this is my first time installing ubuntu. i have been useing it on the live cd and it worked like a dream.
4) umm my hard drives are SATA so there is no special config i think.
5) i have windows xp home edition.
You can use the Super Grub Disk to restore your Window's IPL to your Windows hard drive's mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Once you do this and can boot Windows, you might try reinstalling Ubuntu to the other drive, but select it to boot before your Window's drive in bios...when you reach the grub install page, click on the "Advanced" button, then enter to install grub to /dev/sdb, or whatever the drive you're installing Ubuntu on is designated.  At least if you want to try Ubuntu again, you'll still be able to boot into Windows by booting to it first...did you try booting into recovery mode on your installed Ubuntu and what video card do you have?

---

