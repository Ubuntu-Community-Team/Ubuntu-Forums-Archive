---
title: "Rebooting Problems"
date: 2007-01-31
forum: General Help
---

### Post by aerol on 2007-01-31
Hello all.

I am a new Ubuntu (Edgy Eft) user and am having trouble restarting my PC.  I have a HP Pavilion a640n (Athlon 64 3400+, 1GB RAM, nForce 3 150), motherboard information can be found [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00064822&lc=en&cc=us&dlc=en&product=426323&lang=en#").

I installed Edgy (32-bit version) on a separate hard drive from my Windows XP drive.  After the installation and updates, Ubuntu prompted me to restart.  Ubuntu appeared to shut down cleanly, the power cycled on my machine, and then nothing happens.  The screen goes blank (and the monitor actually goes into power save mode) and there is no hard drive activity.

Hitting the reset button on the PC will cycle the power again, but the same result occurs.  I actually have to completely turn off the power to the system, then turn it back on again to boot into anything.

To see if the problem persisted after the updates, I logged back in and attempted restarting again.  The same problem occurred. 

I had this problem before with Windows XP after installing SP2.  After hours of correspondence with HP tech support, in order to solve this issue I had to simply change my Power Management profile in the Control Panel to anything but the default "Energy Star" setting, and all was well.

I wonder if there is a similar artifact causing this issue with Ubuntu.

Any help will be appreciated.

---

### Post by Mithrilhall on 2007-01-31
I've been having the same problem since installing Edgy.

Anyone have any suggestions?

---

### Post by aerol on 2007-01-31
Bump.

---

### Post by codejunkie on 2007-02-03
> **aerol said:**
> Hello all.

I am a new Ubuntu (Edgy Eft) user and am having trouble restarting my PC.  I have a HP Pavilion a640n (Athlon 64 3400+, 1GB RAM, nForce 3 150), motherboard information can be found [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00064822&lc=en&cc=us&dlc=en&product=426323&lang=en#").

I installed Edgy (32-bit version) on a separate hard drive from my Windows XP drive.  After the installation and updates, Ubuntu prompted me to restart.  Ubuntu appeared to shut down cleanly, the power cycled on my machine, and then nothing happens.  The screen goes blank (and the monitor actually goes into power save mode) and there is no hard drive activity.

Hitting the reset button on the PC will cycle the power again, but the same result occurs.  I actually have to completely turn off the power to the system, then turn it back on again to boot into anything.

To see if the problem persisted after the updates, I logged back in and attempted restarting again.  The same problem occurred. 

I had this problem before with Windows XP after installing SP2.  After hours of correspondence with HP tech support, in order to solve this issue I had to simply change my Power Management profile in the Control Panel to anything but the default "Energy Star" setting, and all was well.

I wonder if there is a similar artifact causing this issue with Ubuntu.

Any help will be appreciated.

i have the same hardware except for the motherboard mine is a Biostar instead of ASUS and i was having the same problem under feisty, but this may also work for edgy. i had to disable **powernowd** you can do that by going to System/Administration/Services and uncheck the box for **powernowd**.

---

### Post by aerol on 2007-02-03
> **codejunkie said:**
> i have the same hardware except for the motherboard mine is a Biostar instead of ASUS and i was having the same problem under feisty, but this may also work for edgy. i had to disable **powernowd** you can do that by going to System/Administration/Services and uncheck the box for **powernowd**.

Ahh that did the trick.  Thank you so much for your help.  I originally started messing with the ACPI and APM settings thinking they were the culprit and banging my head against my desk :) .

Thanks a million my friend \\:D/ .

---

### Post by Mithrilhall on 2007-02-04
Well...I figured out my problem. 

I was trying to get DVDShrink and DVD Decrypter working the other day and kept running into problems.

My DVD burner kept showing up as hdc even though I only have 1 drive. Turns out my DVD burner was set to Master but it was plugged into the IDE2 slot on my motherboard.

After moving the burner to IDE1 and editing my fstab file (I changed '/dev/hdc' to '/dev/hda') DVDShrink, DVD Decrypter and rebooting worked pefectly.

---

