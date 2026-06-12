---
title: "PLEASE HELP! stuck in GPU lockup"
date: 2013-01-24
forum: General Help
---

### Post by Goast on 2013-01-24
So for some reason after trying to update to the experimental nvidia drivers... I've gotten stuck into GPU lock up... the worse part, it seems to effect when I try to use a live CD.  IS my GPU ruined now?  Please help, because now I can't seem to get back to a command line, nothing works.  It just constantly flashes the same screen about GPU lockup failed to idle channel 1.  Won't even let me get to the grub menu.  Refuses to boot from another live cd. I've tried Mint, Xubuntu, and Crunchbang for good measure.
It always becomes all glitchy and purplely.

---

### Post by Double.J on 2013-01-24
Don't panic. It is incredibly unlikely the driver has done anything to your gpu. If the PC turns on and you see the motherboard splash come on, the gpu is working. The chances are it isn't booting from the cd, so double check e boot order. To boot from an optical disk drive it is sometimes necessary to reboot not cold start, so enter the bios anyway and check the boot order then save and exit; this forces a restart. 


Also serif you are able to get into the recovery mode without the live cd

[Ubuntu wiki]("http://https://wiki.ubuntu.com/RecoveryMode")

---

### Post by Goast on 2013-01-24
Well it seems to effect ever attempt at a live cd.  All the GUI's are all glitchy and purple.  I just managed to do a re install same... deal.  I switched monitors even.

Whats going on? Why does the GPU lock up not go away after I re-install or switch distro's?  Why is it all glitchy now? Even if I put in a Debian live cd?

Edit: Just an update, so I can now get it to boot off live CD's but the gpu error still happens and my screen glitches out. although now I can get to the recovery grub... what should I do?

---

### Post by Goast on 2013-01-24
Any suggestions, any distro I can run to try fix it? Every GUI gets graphical glitches, I've tried everything I can.

---

### Post by Double.J on 2013-01-25
> **Goast said:**
> So for some reason after trying to update to the experimental nvidia drivers... I've gotten stuck into GPU lock up... 

Okay, you've confirmed it's booting off the live cd and not the internal hdd? And you reinstalled, did the display work correctly during the install? 

If the problem persists in a live environment, and you did not have the same issue with your card and that live cd before, then it is going to be the card I'm afraid. Think back, did you change anything else between powering on the computer the day you updated the driver and shutting down? Nvidea firmware, gpu settings? Graphics settings at the bios level? The driver itself is specific to an OS so changing the driver in oneOS can't affect the performance in another OS, but it is possible through things such as overclocking to make changes that affect all. 

Rule out/in the card by powering down and removing the card. Connect the monitor to the motherboards video out. Cards do fail from time to time, more likely if they are regularly run above their designed spec, but it'd be one heck of a coincidence to fail the exact time you installed a driver.

---

