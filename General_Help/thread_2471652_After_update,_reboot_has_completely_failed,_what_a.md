---
title: "After update, reboot has completely failed, what are my next steps?"
date: 2022-02-05
forum: General Help
---

### Post by goemonburo on 2022-02-05
I clicked "Update" last night and saw that a fairly lengthy bunch of packages were updated in my Lubuntu 20.04LTS desktop (A Dell XPS8910).  I rebooted to find that it is apparently not even getting to even a boot manager.  The screen goes black, the system shuts off, comes back on and the screen stays completely black, I don't even see a Dell splash screen...and then it seems to switch into hibernate, with the little orange LED in the power switch flashing.  That's the only "life" I can see in the system at all:  A little flashing LED.  Keyboard presses, mouse input, nothing has any effect.  No disk drive whirs, nothing that indicates it's got any processes happening.  

I tried seeing if it was something it had to "run through" by leaving it for 2 hours, but after 2 hours it was still the same.

I had a Live USB on hand so just plugged that in and it booted on the USB just fine.

I don't recall this ever having happened before, so what are my next steps?  Should I try to revert to an older kernel and see if it boots with that?  Can I poke around with the Live USB to check things and figure out what's going wrong?  Are there any commands to "roll back any updates" so I can have a working system again?  My hunch is that it was the update that did it.  I don't think it's hardware failure or I wouldn't be typing this right now.  

Thank you in advance for the help.

---

### Post by HermanAB on 2022-02-05
1. Use the install USB widget and make a backup of your data.
2. Once your data is safe you can experiment to try and revive the system, or
3. Reinstall (probably the quickest solution).

---

### Post by grahammechanical on 2022-02-05
If the live session loads then that will be confirmation that some of the hardware is not broken. Is the motherboard set to look for an OS on a USB memory stick before it looks for an OS on a hard drive? You may need to enter the UEFI/BIOS settings utility to get the motherboard booting from the USB memory stick. Do you know how to do that?

[https://www.isunshare.com/windows-password/how-to-set-your-computer-to-boot-from-usb-drive.html#opt4](https://www.isunshare.com/windows-password/how-to-set-your-computer-to-boot-from-usb-drive.html#opt4)

Are you dual booting? Pressing Esc should bring up the Grub boot menu. On my new Linux laptop which is not dual boot pressing Esc brings up the Grub menu with these options: Ubuntu; Advanced options for Ubuntu; UEFI Firmware Settings. If you get a menu like that you have choices. Use Advance Options to load an older kernel or recovery mode or both. Or, change the boot order to load the live session.

Regards

---

### Post by guiverc on 2022-02-05
I have no idea, but I'll give some thoughts.

Ubuntu 20.04 LTS in recent week(s) switched to using the 5.13 kernel stack from 21.10,  **IF  **you're using the HWE kernel stack.

*- stack description - skip if you know it*
*Ubuntu LTS releases offer two kernel stack choices; GA is the more stable stack and remains on 5.4 for the life of 20.04, and with Lubuntu it's the default for installs using Lubuntu 20.04 & 20.04.1 media. HWE is the hardware enablement stack which changes during the first ~2.5 years of the product; ie. 5.4 switched to 5.8 from 20.10 at 20.04.2, 5.11 at 20.04.3, and is in state of moving to 5.13 or the full 20.04.4 stack; this change to 20.04.4 is still in progress.  Lubuntu 20.04.2 & later media defaults to HWE stack by default.  Refer [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) but do note Lubuntu is more like Ubuntu 18.04 LTS with regards media, and not like Ubuntu 20.04 LTS Desktop.*

If you're using the HWE stack; problems can occur when changing stack; but I'd still expect you see `plymouth` (*how it appears is box/firmware specific; but I'm guessing your box would be black flash, dell logo, black flash then lubuntu older plymouth).  Grub menu may not appear if you've only got a single OS installed on the box*), but it's possible you don't.  

If you can get `grub` to appear; and you're using HWE kernel stack as my thinking here goes, I'd select a 5.11 (20.04.3 kernel stack) and hope that would boot normally; ie. your issue is the newer 5.13 kernel; and we've got something to work with at least.

How you get `grub` to show can be SHIFT, or hitting ESC (*once*) after your systems POST runs, or before `plymouth` (or black screens/flashes) occur. Hitting it at the right time can be tricky though; some some faster boxes I need multiple reboots to get it right (*on other boxes I get it first time*).  Prior replies have mentioned `grub` so I'd use what they said.

If you want to confirm using *live* media; I can provide a [link to 20.04.4 daily]("http://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/focal-desktop-amd64.iso")  which I'm guessing you'll have troubles with **IF what I'm thinking is correct  ** (no guarantees here; it's just a thought!) and be different  to your older *live* media. The *daily* ISO I provided a link for contains the 20.04.4 kernel stack (ie. 5.13 kernel).

This is just my thoughts (ie. *what I'd likely explore*) - sorry I have no answers.

*Limits in my thinking:   How often do you update/upgrade; if you're like me & check for upgrades 3+ times per day this thinking is of no value, my thinking will more likely be correct if you've not updated in 5-12+ days or more, ie. when did you last `apt full-upgrade`* ?

---

### Post by Impavidus on 2022-02-06
Using the live disk, you can view the logs of the installed system. Have a look at the dpkg log (/var/log/dpkg.log) to see which packages were updated. Any packages related to booting?

A fresh install is the fast way out, but it may be nice to know what went wrong, to prevent if from happening again.

---

### Post by zebra2 on 2022-02-06
It is possible that you had "Proposed" enabled in the repositories.  On occasion Proposed has presented large updates that I suspected to be undesirable. In those cases I exit the update. Open the repositories and disable Proposed and then refresh the updates and then run Update. Don't know what you have going on but that is my best guess.  In addition, I have my /home installed on a separate partition which allows me to reinstall without tampering with the /home partition and it's data. With /home isolated in this manner there is two ways to easily reinstall. One method formats /root and the other preserves /root.  the second option will get you a running system with very few changes.  The first option is only needed if the second option fails.  Again it is advisable to have a /home on its own partition especially if Proposed is enabled. Be cautious with very large updates. Update from the command terminal only and look at what is going to be deleted. If your desktop is in the "to be deleted" list, be careful.

---

