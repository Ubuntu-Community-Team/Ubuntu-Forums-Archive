---
title: "Re-Installing on Toughbook"
date: 2016-06-06
forum: General Help
---

### Post by the.ashling on 2016-06-06
Panasonic CF-18.  Belonged to a friend who loaned it to an ex while she wasn't an ex.  Luckily, it's usable as is, but...  Software is so out of date it's scary, and can't update **** unless you know the pw.  Neither he nor I know the pw.  I'm trying to reinstall over it with the newest Ubuntu to get rid of the profile and start out new, but it's not seeming to allow me to load/install from my passport with Ubuntu on it.  I've never had this issue with any of my comps running Linux, but I've never used a toughbook before either.  I thought I got it to load using the BIOS, but it loaded right back to the hard dive loading with her profile.  Any feedback or suggestions would be more than welcome.

---

### Post by Bucky Ball on 2016-06-06
How are you trying to install Ubuntu, exactly? You have burnt the ISO to a bootable USB or disk? Which release and flavour are you trying to install?

---

### Post by the.ashling on 2016-06-06
Trying to load/install it from my WD 1tb external hard drive, 16.04 Ubuntu.  It worked to install over windows on my own computer, but this tb just doesn't seem to want to touch it.  I tried deleting everything, reformatting the external drive and reinstalling it using the toughbook onto the drive, to see if that would help - still not loading.  I'm worried the version is just so old it's trying to fight it.  It's currently got 11.1 installed.

---

### Post by Bucky Ball on 2016-06-06
You have done it this way before? Could you please explain exactly what you have on the external drive and the steps you are taking to try and install. Do you have the install ISO on the external drive or have you actually installed Ubuntu onto that drive and are trying to install that to the internal drive.

Sorry, bit confused about how you're doing this. Installing from a hard drive is not the usual course. You don't have a USB or DVD to do the job?

---

### Post by the.ashling on 2016-06-06
No, it's completely fine, I was a bit vague.  Initially, I had it installed on the hard drive as a complete I can run a computer from this portable hard drive(phd), A Western Digital MyPassport Ultra, 1TB.  Now, honestly, not so sure.  My computer's hard drive died, needed to replace it for too long, was about to order new and was working off of this one untill I could get new when my mobo went out, and my friend is loaning me this one so I can use it and get it so that he has control of the admin acct on it b/c it can't get updated w/o it.  I went ok, I can run it from the phb and do a clean install, I tried to run from the phb by reversing the BIOS order, making it go to USB first before hard drive, but it never loaded.  I just got a black screen with a blinking underscore for an hour.  I went ok, maybe go by reinstalling onto the phb.  I'm not completely sure what this thing did, but it let me download the ISO into the downloads folder, but wouldn't let me run it.  So I tried just xfering it over to the phd to see if it will do anyways, no go.  Same black screen with blinking underscore.  Used to have a USB to do the job, have a DVD, but this thing doesn't have a CD or DVD drive, and I don't have an external.  The phb has been working as just an oversized USB for me since mine got lost.

---

### Post by X-RED_Tech on 2016-06-06
If [this]("http://www.tabletpcreview.com/tabletreview/panasonic-cf-18-toughbook-tablet-pc-review-pics-specs/") is the machine you're trying to use I have bad news. Only a very light distro can run acceptably.

And if your portable installation is 64-bit then it couldn't possibly boot in the 32-bit Pentium M Panasonic.
You have to make a USB flash from another computer: Download the ISO (Lubuntu is probably the best candidate in the Ubuntu family), follow this instructions - [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) - and boot from it in order to install. Or use the ISO to burn a DVD but I'm not sure that rugged series came with it. It should also boot from an external USB CD/DVD drive.
In a nutshell, there's nothing you can do with your current installation of Ubuntu in the external HDD.

---

### Post by the.ashling on 2016-06-10
Ok, installed 32-bit Lubuntu with the ISO onto a thumb drive on a friend's computer, put it in, F2, set to boot from usb first in BIOS...  This thing is still loading from the hard drive.  Seems to be ignoring anything plugged into the usb drive and goes straight for the hard drive.  The toughbook doesn't have a dvd or cd drive, don't have an external, but even if I jeryrig something using my sata-usb with the one I do have, I think it might have the same issue - ignore the USB until it's booted from hard drive.

---

### Post by X-RED_Tech on 2016-06-10
Even hardware of that age without an internal USB drive used to boot from USB. How would you install an OS, any OS, if you can't boot from the installation media?
How you "[COLOR=#000000]installed 32-bit Lubuntu with the ISO onto a thumb drive" is most likely the problem here.
Several options depending on the OS where you'll be making the installation media: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)[/COLOR]

---

### Post by the.ashling on 2016-06-10
That's what's got me confused - I've gotten an older machine than this to boot from USB.  I dun get it.  I'll try installing it with rufus again, and follow that help page, I'll post later.

---

### Post by X-RED_Tech on 2016-06-10
If using Rufus then make sure you select MBR in the options.

---

### Post by the.ashling on 2016-06-12
Well, with permission of the real owner, i pulled the drive, plugged it back in when it started to finally load from usb after turning it off again, turned it back on, loaded from usb.  Had to get help from a repair place to get the instalation on the drive done, the guy knew rufus and used it, unsure how bc their store rules dont let customers see the store computer screens...  anyways, got it to load, had to forcepae to install, but it installed.  After i got it to load to homescreen, restarted to be sure it was working without the thumb drive.  So then went ok...  working, we can upgrade the programs requesting it.  It requested restart after install.  Hit restart....  It turned 'off' but never turned back on.  With this unit, everything but battery charge light will at least flash off.  Left it an hour, still locked.  Held the power button untill it turned off, then restarted...  Now its giving me an error i cant find a fix for.  The last retry states, "[111.631896] [drm:intel_cpu_fifo_underrun_irq_handler [i915] *ERROR* CPU pipe A FIFO underrun"  and only that line ...  and its doing this with loading from the hard drive, and run from usb without installing, I can get it to reinstall, but it goes to restart and gives me the same issue with the restart.

---

### Post by the.ashling on 2016-06-12
Tried another reinstall.  Forced pae, and it seemed to install fine till the reinstall.  Loading a black screen, saying:

/dev/sda1: clean, 121544/2411920 files, 797162/9638565 blocks
[    41.728194] [drm: intel_set_cpu_fifo_underrun_reporting [i915]] *ERROR* pipe A underrun

Jeeze, such an adventure for what was supposed to be a simple reinstall.

---

### Post by X-RED_Tech on 2016-06-12
Nothing simple about trying to fit a current distro release into such archaic hardware...

The error you're seeing is supposed to be a warning only so it shouldn't prevent normal boot. What most likely isn't starting is graphics because that machine simply don't have the specs to run any modern standard Ubuntu. Lubuntu perhaps but even lighter would be preferable.

---

### Post by the.ashling on 2016-06-12
So find an older version of lubuntu and attempt that?

---

### Post by X-RED_Tech on 2016-06-12
No, always use supported releases. 
And I'm really not sure about Lubuntu working acceptably with only 512MB RAM.

---

### Post by the.ashling on 2016-06-13
Min requirements are less.  Perhaps without the extra programs it requests to install.  The user after me will just need to browse for homework, so being able to view video and listen to music isnt a must.  It seems like updating those caused the last issue, anyways.  Itd been working fine till they updated, not sure how its affecting the newer installs still though, since I overwrote the drive.

---

