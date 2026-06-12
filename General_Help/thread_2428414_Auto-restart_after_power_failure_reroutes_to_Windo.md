---
title: "Auto-restart after power failure reroutes to Windows install vs Ubuntu's...."
date: 2019-10-03
forum: General Help
---

### Post by jh20001 on 2019-10-03
Hopefully, someone has experienced this. 

I have a mini PC (Azulle Byte3) that originally (and still does) came with Windows 10 installed. I wanted to keep Windows, so I dual booted with the latest Ubuntu on another partition. In BIOS, I have it set in boot order to start with Ubuntu (as I want it to power on right to Ubuntu's loader), and Windows as second. I can shut down, restart and do whatever I want, and it goes right to Ubuntu's loader. 

However, I then start having issues with the smart plug. It likes to auto update its firmware on its own (no way to turn it off). When this happens, it of course cycles and I lose the mini PC until I get home to manually turn it back on. I can't have this since I have PiHole running on that machine, so everything on the network that isn't IP dependent, loses connectivity to the internet. 

So I set BIOS to auto-start after power outage, thinking this will save all of my woes. Again, I can manually restart, shutdown, etc...and it goes to Ubuntu. However, when I cut power to the outlet and then bring it back, it does start, but Windows completely takes over. Bios settings are changed to go to Windows instead of the ubuntu loader (the order) and boots into Windows 10. I check BIOS, and the boot order shows windows then Ubuntu. I switch it back, save it and reboot and it goes to Ubuntu. However if I cut power to the outlet and then power back on again...Right back to Windows and the changed bios settings. How the heck, is the auto-boot after power outage function causing all of my BIOS settings to change and boot to Windows? I don't want to have to be forced to strip Windows from the machine since getting it back is a real PITA. 

Has anyone else run into this issue? 

Thanks.

---

### Post by Skaperen on 2019-10-04
i have heard of this issue before.  it seems to always be with computer brands i have never heard of and they always have Windows installed.  Microsoft can push these small companies around and make them use specific logic in their BIOS that really is intended for security.  they could be assuming the BIOS settings might be a hack attack and intentionally restoring them to factory settings.  or it could just as easily be bad BIOS setup by the manufacturer.

---

### Post by jh20001 on 2019-10-05
> **Skaperen said:**
> i have heard of this issue before.  it seems to always be with computer brands i have never heard of and they always have Windows installed.  Microsoft can push these small companies around and make them use specific logic in their BIOS that really is intended for security.  they could be assuming the BIOS settings might be a hack attack and intentionally restoring them to factory settings.  or it could just as easily be bad BIOS setup by the manufacturer.


That was one theory I had rolling around in the back of my mind. It would be terrible if so since it is so convenient to have that small little box run the server. I do have a PC that runs 24/7 but it has other things to worry about, like video encoding. The last thing I want to do is setup a VM on it just for this. No matter the resources I set to the side for it, that's less resources for encoding and other tasks.

---

