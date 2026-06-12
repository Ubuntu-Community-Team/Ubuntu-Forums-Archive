---
title: "Can not boot without going into BIOS and &quot;save + exit&quot;"
date: 2022-05-01
forum: General Help
---

### Post by Jonners59 on 2022-05-01
Have had an odd one here for a few weeks now.  When I boot my laptop it goes into the GRUB command line.  If I reboot into BIOS at boot up and then just select "F10" (Save and Exit) it then boots normally.  The next time I have to repeat the process.

---

### Post by oldfred on 2022-05-01
What brand/model system?
Does laptop have latest UEFI from vendor?

UEFI or BIOS install?
You may have UEFI set for one mode (UEFI or BIOS) & for one time it may allow boot in the other mode?

This will not show most UEFI settings, but may show a configuration issue?
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Jonners59 on 2022-05-01
> **oldfred said:**
> What brand/model system?
Does laptop have latest UEFI from vendor?

UEFI or BIOS install?
You may have UEFI set for one mode (UEFI or BIOS) & for one time it may allow boot in the other mode?

This will not show most UEFI settings, but may show a configuration issue?
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks OldFred.

> **oldfred said:**
> What brand/model system? GF63_Thin_9RCX with Windows 10 and xUbuntu which is up to date
> **oldfred said:**
> Does laptop have latest UEFI from vendor?I believe it does
> **oldfred said:**
> You may have UEFI set for one mode (UEFI or BIOS) & for one time it may allow boot in the other mode?  Don't know.
> **oldfred said:**
> This will not show most UEFI settings, but may show a configuration issue?OK, noted.  I guess next is how to find out.
> **oldfred said:**
> Please copy & paste the pastebin link to the Bootinfo summary report  ( do not post report), do not run the auto fix till reviewed.Lets see  details, use ppa version with your USB installer (2nd option) or any  working install,  not Boot-Repair ISO [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)  OK, I need to work this one out.  I'll need to revert.

---

### Post by GhX6GZMB on 2022-05-01
I suspect you have a bad CMOS battery.

---

### Post by oldfred on 2022-05-01
If clock resets to default, that is a sure sign of bad battery.

My laptop from 2006 has that issue. 
But I retired it and only installed 20.04 to see if it still worked. Ubuntu did not, but Kubuntu and server versions did.

---

### Post by Jonners59 on 2022-05-02
No, the clock doesn't reset and all other settings remain, so I don't think it's that.

---

### Post by Jonners59 on 2022-05-23
> **oldfred said:**
> What brand/model system?
Does laptop have latest UEFI from vendor?

UEFI or BIOS install?
You may have UEFI set for one mode (UEFI or BIOS) & for one time it may allow boot in the other mode?

This will not show most UEFI settings, but may show a configuration issue?
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Sorry, Fred for taking so long to reply.  I have had so many things to deal with and then can't get the laptop to boot into the USB storage.  Anyway, fortunately, I started playing around and fixed the problem without the need for Boot Repair.  I found that when I turned off "Fast Boot" it all worked.  So sorted.  I now need to fix the other problem, not being able to boot into the Ubuntu OS for which I have another thread...

---

### Post by oldfred on 2022-05-23
Fast Boot is an UEFI setting that assumes no system changes. That almost always has to be off when installing.
You can "cold" boot or from full power down, boot, so UEFI then does a normal boot, one time. 
Often with fast boot on, you do not have time to press any keys to get into UEFI or get into UEFI boot menu as system does not do a full POST scan of system.

---

### Post by Jonners59 on 2022-05-24
> **oldfred said:**
> Fast Boot is an UEFI setting that assumes no system changes. That almost always has to be off when installing.
You can "cold" boot or from full power down, boot, so UEFI then does a normal boot, one time. 
Often with fast boot on, you do not have time to press any keys to get into UEFI or get into UEFI boot menu as system does not do a full POST scan of system.

Thanks, OldFred
Always coming to the rescue.  I bet you wear your pants on the outside of your trousers.  :-)

Just need someone to help with the other issue now:  [https://ubuntuforums.org/showthread.php?t=2474509](https://ubuntuforums.org/showthread.php?t=2474509)

Best
Jonners59

---

