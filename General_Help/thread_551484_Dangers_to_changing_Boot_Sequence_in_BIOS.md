---
title: "Dangers to changing Boot Sequence in BIOS?"
date: 2007-09-15
forum: General Help
---

### Post by Stan_1936 on 2007-09-15
I am planning to try out Ubuntu on a laptop which is not set to boot from CD in the BIOS because I tried it and nothing happened.

1.  Are there any dangerous sideffects to changing the Boot Sequence in th BIOS?  Files have been backed up and I'd like touse the LIVE-CD for around a month and then install.  Could changing the BIOS settings for Boot sequence cause problems?

2.  Instead of using a CD to burn the ISO, would the LIVE-CD run faster if I used a DVD...so it would be a LIVE-"DVD"?

---

### Post by forestpixie on 2007-09-15
changing the bios to boot cd first won't cause any problems that I've heard of - it'll just look there first.

don't know if it'll be faster using a dvd - once it's loaded into memory I believe increasing RAM would make it faster

have fun :)

---

### Post by Stan_1936 on 2007-09-15
I think I should haveenough RAM but was wondering whether the actual responsiveness of the system would be better off(faster) using a DVD rather than a CD?

---

### Post by AusIV4 on 2007-09-15
I assume you're saying, have it try to boot from the cd drive before it boots from the hard drive, right?

The only real danger of having your PC boot the CD first is that if someone gains physical access to your computer, they can boot a Live CD and have root access to all of your files. That aside, you shouldn't have any problems changing the boot sequence back later on.

I don't think burning to a DVD instead of a CD will be any faster. There might be miniscule improvements related to lower seek times (I'm not really sure), but any time the drive has to spin up is going to be quite slow while it finds what it's looking for.

Lastly, are you talking about running your computer just from the live CD for a month, or are you talking about using it off and on for a month before installing? As much as I like the Live CD for recovery purposes, I really don't find it to be a good sample of what the operating system is like. It doesn't begin to demonstrate the performance capabilities of the OS, since you can't save to it, you can't really experience the OS once you've customized it to your needs. Basically, don't get too discouraged if the Live CD doesn't impress you too much.

---

### Post by Stan_1936 on 2007-09-15
Just running it of and on for a month to see hwo the system responds to it.

Thanks for the info.

---

### Post by rivalarrival on 2007-09-15
1. There is only one possible danger that I can think of, and I don't think it applies to your situation.

In a shared-computer situation - like a public library or internet cafe - you don't want people to be able to boot their own operating system and bypass your local security policies.

Considering that this is your laptop and you're talking about possibly installing a new operating system, I don't think this is a concern. The only other effect you'll notice might be an additional couple seconds to your normal boot sequence. 

2. It might be a little faster, but probably not significantly. The Live-CD is basically an emergency recovery device. It gives you a means to get your computer up and running, do some research on the internet, access the files on your hard drive... 

You lose the ability to make any changes to the basic setup. You can't save your settings or customizations. You can't install other software with a package manager (one of the coolest features of Ubuntu) - In my opinion, the LiveCD is pretty lousy for long-term evaluation purposes. 

If you want to try-it before you don't-buy-it (hehehe) and make as few changes to your current system as possible, look into Wubi. It allows you to install Ubuntu from Windows without making any changes to your hard-drive partitions. 
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by tgalati4 on 2007-09-15
The Live CD will give you a clue as to what doesn't work and what needs fixing.  Most problems have work-arounds so that you can get all of your hardware working.

For instance if you have a finger-print reader on your machine, chances are the Live CD will not detect it and load the driver.  If it does, great!  If not, then you will need to search the forums for things that others have tried.

Things you may encounter:

Can't get the full screen resolution.

Can't get wireless to work.

Can't get the audio-buttons to work.

Can't get the CRT-TV-out switch to work.

Can't get touchpad to act smoothly.

Can't get it to hibernate or suspend or wake-up properly.

After a few days, you will discover what doesn't work out-of-the-box and how much work is involved in fixing.

---

### Post by Stan_1936 on 2007-09-15
Well, I found this link which is pretty much causing hesitation with the BOOT sequence change, as I am usingthe same model of laptop:

[http://ubuntuforums.org/showthread.php?t=178545](http://ubuntuforums.org/showthread.php?t=178545)

---

### Post by rivalarrival on 2007-09-15
You just won the lottery </sarcasm> 

I must've worked with over 200 different machines in the past 10 years - not a single one EVER had a problem in changing the boot order - it is one of the most innocuous of possible BIOS changes.

Getting it to boot often turned into an issue: broken MBRs, corrupted loaders, fried USB keys, "coastered" CDs... but these are all temporary conditions and easily repairable IF you can boot to something else. 

If the problem is widespread, that laptop should've been recalled. That's an absolutely ridiculous problem.

---

### Post by Stan_1936 on 2007-09-15
well, that's reassuring.  My significantly older desktop booted from CD fine.  Odd that a newer model won't.

---

### Post by rivalarrival on 2007-09-15
If bios isn't set to boot from the CD, it's not going to boot to the CD.  If you can't change that setting, you can't use the live-cd or the CD installation methods.

Wubi will still work, even if you can't boot from CD!

Still, you should either get that problem fixed (the thread you linked mentioned a BIOS update that should solve it) or be ready to use a work around (one of the comments suggested you could pull the coin-cell battery that maintains the BIOS data for a few moments, fixing the error) BEFORE you have a major problem. (Like a hard drive crash, boot sector error, or corrupted windows installation - if you do have that BIOS bug, you won't be able to fix those problems without some major surgery and digital acrobatics.)

EDIT:
Bios update for Inspiron 6400 / E1505 dated Jun 2007 SHOULD solve/prevent the problem in the thread you linked. You might want to check out the rest of the drivers while you're at it.
 
[http://support.dell.com/](http://support.dell.com/)

---

