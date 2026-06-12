---
title: "[SOLVED] Please Tell Me it's Not That Bad..."
date: 2008-01-03
forum: General Help
---

### Post by kmac on 2008-01-03
Alright, I'm Dual-Booting WinXP and Feisty. Last night, I booted into Feisty and started my every-day bad habit of stumbling. Suddenly, I had no response whatsoever from my computer and it was completely locked up. I couldn't even change into another vitrtual terminal. So I waited a while and nothing let up so I cold-killed it. Trying to boot back up, my machine got stuck at the splash screen then switched to a black screen with nothing but a cursor in the top left. I cold-killed again and repeated this process maybe twice more. I tested my windows bootup and it booted fine, so I restarted and went again at my Feisty. Recovery mode gets stuck at bootup as well, and after letting bootup sit for a while I eventually get some errors:

Attempting to manually resume...

hda: Timeout while waiting for DMA


Then she spills a lot of errors claiming not being able to read blocks, then a few more saying that certain paths could not be mounted either because of bad arguments or the files do no exist. We wrap it up with:

/bin/sh: can't access tty: job control turned off.

And then sh comes up as the user "initramfs" where only a few select unix commands seem to work.


Please tell me my HD is not dead and this is somehow saveable :( 

--Kyle

---

### Post by amdalex on 2008-01-03
I think you might need to reinstall fiesty.:confused:

---

### Post by kmac on 2008-01-03
Is there any way of doing that while still being able to keep my existing data?

--Kyle

---

### Post by p_quarles on 2008-01-03
If Windows is all right, then it's certainly not a complete hard drive failure. Possibly some corrupted blocks, but that's not "that bad." 

Anyway, I'd suggest using the installation disk to boot up into "System Rescue Mode." From there, you should be able to run fsck to scan and attempt to repair your filesystem.

---

### Post by bigken on 2008-01-03
I would boot into windows backup my data 

install [this]("http://www.fs-driver.org/") in windows see if you can read your  linux partitions  and recover  your data  

then go to the makers web site and see if there any tools to test your drive

---

### Post by kmac on 2008-01-03
Well hate to be so pessimistic, but Windows no longer works all of a sudden. I get stuck at the Windows splash no matter how long it sits there. I have hope because it was working before, and I'm not getting BSOD or anything.

--Kyle

---

### Post by bigken on 2008-01-03
do you have another hdd to install window on and set your old drive as a slave


did your try pessing F8 and boot into safe mode

---

### Post by kmac on 2008-01-03
I have an external enclosure but I'll try getting into safe mode first.

--Kyle

---

### Post by kmac on 2008-01-03
OK, BSOD from Windows...  :(

Trying external enclosure, I'll post again later and let you know how that goes.

--Kyle

---

### Post by p_quarles on 2008-01-03
Try the boot disk idea. Using that, you'll at least get a picture of what's wrong with the hard drive, and to what extent.

---

### Post by LinuxGuy1234 on 2008-01-03
I would boot into Fedora and backup my data.

---

### Post by kmac on 2008-01-03
What do I look for? If I bott with the boot disk.

--Kyle

---

### Post by p_quarles on 2008-01-03
> **kmac said:**
> What do I look for? If I bott with the boot disk.

--Kyle
When the menu comes up, you'll want to select "System Rescue Mode."

The only catch is that this option *might* only be available on the alternate installation CD. I can't remember.

---

### Post by bigken on 2008-01-03
dont mess with bad hdd you might make things worse try and get you data 1st 
using another drive with a working OS

---

### Post by kmac on 2008-01-03
Ok well this could be bad... My computer refuses to boot from CD. I checked setup and everything is fine, but it still loads to grub and continues to try to boot Feisty.

Just a bad day...

--Kyle

---

### Post by p_quarles on 2008-01-03
Can you get into your BIOS? You might need to set the system to boot from the CD. 

If that doesn't do it, this is starting to look more like a hardware problem, and one that goes deeper than just the hard drive.

---

### Post by kmac on 2008-01-03
BIOS are set: Floppy, CD-Rom, HD.

No floppy drive on my laptop, though... which makes that interesting.

This is me: Sitting at my WORKING computer, typing all my problems up, eating a leftover burger from Applebee's with a bottle of Coors light while my roommates rock out to Guitar Hero III and my computer is as dead as a doornail...

Life just gets you like that sometimes...

--Kyle

---

### Post by landrash on 2008-01-03
If you have access to another computer and a way of connecting the hard drive to that computer thats the way I would goo. 

Since it seems to become worse and worse just try to backup your data before you do anything else. My guess would be that your hard drive is on the brink of death. 

Good luck.

---

### Post by p_quarles on 2008-01-03
> **landrash said:**
> If you have access to another computer and a way of connecting the hard drive to that computer thats the way I would goo. 

Since it seems to become worse and worse just try to backup your data before you do anything else. My guess would be that your hard drive is on the brink of death. 

Good luck.
Possibly, but given that the CD drive doesn't seem to want to boot, I'm beginning to wonder if it's the motherboard. 

On the one hand, that's just as bad. On the other hand, that may mean that you haven't lost any data. Either way, though, it doesn't sound like much fun.

---

### Post by kmac on 2008-01-03
*Cries*

Think I'll need something stronger than Coors Light. Then I'm calling into work saying that there was a death in the family.

--Kyle

---

### Post by kmac on 2008-01-03
MIRACLES DO HAPPEN!!!

I think someone heard my prayers, or maybe this is all just a dream. But I eventually had given up on my computer and proceeded to just leave it on (forgot to shut it down) and sit on my couch drinking beer and watching my roommates play Guitar Hero. So, I realized it was powered on so I went to go shut it down and BAM!!! Login Screen. I was like "roflmao nfw omg wtf?" And decided to restart it to make sure. I could feel my AMD smiling at me as she rebooted and happily brought up my Gnome desktop and I giggled myself away into Ubuntu bliss.

--Kyle

---

### Post by xeth_delta on 2008-01-03
I would seriously recommend you to make a back-up of your important data, now that the system is booting. Just in case it stops working again.

Xeth

---

### Post by barney385 on 2008-01-03
That's really strange. Sounds like a possible heat issue to me...

:???:

---

### Post by bigken on 2008-01-03
could have being a bad checksum error in the bios 

like others have said backup while you can

---

