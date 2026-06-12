---
title: "An odd issue, but one that shows Ubuntu is definately more robust than windows."
date: 2008-04-15
forum: General Help
---

### Post by LeoSolaris on 2008-04-15
I did something amusing to my laptop just a few minutes ago. I opted to change something in BIOS about the way the hard drive works to enable the flash cache for the hard drive. (I wish I could recall the letters for it, and I will edit this when I reboot to look at my BIOS settings again)

To make a long story short, Ubuntu didn't even flinch at the changes, if anything it shaved a couple of seconds off the boot time. Windows however is refusing to even load in Safe Mode command line only. I get an odd blue screen, not even the standard "blue screen of death," telling me to do a chkdsk /f, but it will not let me get to the command line to preform such an operation.

I can still access all of my data with Ubuntu, so data loss isn't an issue. I would rather not have to yank all of my data back off the windows partition, since I had it stashed over there for the upcoming Hardy release.

My real question is this... Does anyone have the faintest idea how to fix this? I tried simply switching it back, but that had absolutely no effect. I am going to try out SystemRescueCD and UltimateBootCD in a few minutes. I'll edit in the results. I have the XP disk, but if I re-install, XP will wipe my hard drive entirely, and I can't afford to do that. Are their any other ideas for what is effectively a NTFS data storage partition?

I suppose I could VM Windows, since I only use it to play games, and at that not even high end games. Wine is still a little grumpy about some of my favorites otherwise Windows would have been out the window a long time ago.

Sorry to ask you guys a question about Windows. For all that I have made Windows give some pretty wierd errors, this one is new for me. (If this is in the wrong section, sorry, I wasn't 100% sure where to put it.)

Leo

P.S. Maybe this will ultimately be a good thing. I have been thinking about removing Windows for a while now, and had been looking closer at VM'ing it instead.

[SOLVED]

I get the feeling that eventually I will get rid of XP, but for now I have it working again. Thank you for all of your help! For some reason the first time I tried turing it back to ATA mode, it would not open, but halfway through the boot-up for the XP repair disk (about 2 minutes in) I remember that I forgot to switch it back to ATA again. (Ubuntu was marginally faster)

On a lark I booted XP in "Last known good config" and low and behold, the beast was resurrected! I got a Dr. Frankenstein moment  (you know, "It's alive! It's AAALLIIVVEE!") and now I am letting you guys know what happened.

Thank y'all again!

Leo

---

### Post by forrestcupp on 2008-04-15
You could try undoing what you did in the bios.  Then you could try booting to your Windows disk and do a repair installation, which won't delete your files.  If that doesn't work, [Tech Forums](http://www.tech-forums.net/pc/f9/) is a great active forum for Windows.

As for gaming in a VM, it probably won't work if it is 3D, even if it's an older 3D game.

---

### Post by sdowney717 on 2008-04-15
as windows boots quickly hit the F8 key. And select the one that takes you to a command prompt. I think you can then run chkdsk command. Or perhaps you can boot into safe mode and reboot again.

---

### Post by elmer_42 on 2008-04-15
Look through your history and try to find the guide you followed. Then just reverse it. If you didn't follow a guide, look through your BIOS and see if you remember what you changed. If neither of those work and you need to save your data, get an external hard drive. Boot into Ubuntu and just copy over the files you need to it. Then reinstall Windows and copy it back.

---

### Post by LeoSolaris on 2008-04-15
Thanks guys,

I did try simply undoing it.  What I did was switch my SATA drive out of ATA mode and into AHCI, then enable the Flash Cache. After a bit of Googling, I discovered that the Flash Cache is what allows Vista to use Ready Boost. I tried both SystemRescue and UltimateBoot, but neither one really did the trick.

I get the sneaking suspiscion that I am going to have to reinstall to get it operational. Now that I have a small USB hard drive coming in the mail, I'll save what I need out of it and erase the partition. I think I will just try out virtualizing it. Nothing really extreme lost to tell you the truth.

Thank you for your help guys. I think I made this post more to vent and brainstorm than anything.

Leo

---

### Post by forrestcupp on 2008-04-16
I seriously would try a repair installation before you go wiping the partition and doing a clean install.

---

### Post by LeoSolaris on 2008-04-16
I have never actually tried a repair install. I'll be trying that out when I get home from class today.

(Yes, I abuse the forums while paying through the nose to be educated. Some of these profs though, teach at a snails pace.)

Leo

---

