---
title: "Linux Mint &amp; Ubuntu install fine but will not boot after install."
date: 2013-06-23
forum: General Help
---

### Post by cory72187 on 2013-06-23
So I have this Toshiba Satellite p755 that came with windows 7 at the time.
 
During a bios update the thing freezes for a couple hours and I  eventually am forced to unplug the thing. It turns into a 700 dollar  brick that freezes at the windows screen every time.
 
I decide to just switch to Linux.
 
Load up Mint and everything is going well. the live cd boots up and the  install goes well, everything is great. go through the reboot process,  cd pops out, reboots, FREEZES.
 
I do this a few times before I decide to try ubuntu. same exact thing happens with ubuntu.
 
as a last ditch effort i decide to try the "boot repair disk" at source forge by yannubuntu
 
It ran through its thing and said it did some stuff, but the problem persisted.
 
I am thinking it must be something deeper than the operating system that  im running because all three OS's freeze at the start screen.
 
I thought that perhaps it was the hard drive itself, but then how is mint and Ubuntu able to install at all?
 
I thought maybe bios was messed up, but then how was i even able to start installing anything?

---

### Post by dave0109 on 2013-06-24
It *could* be an BIOS/MBR/EFI boot issue.  On my system, I've got it setup for EFI mode, and if I choose to boot in BIOS/MBR/legacy mode (whatever your system may call it), then I just get a flashing cursor in the top left of the screen.

Perhaps your BIOS update has reset this, but it works OK from the LiveCD because the boot order allows the CD to get picked up.  Doing the installation of Ubuntu/Mint would have worked OK, because the discs are accessible.

I would bring up your BIOS boot order menu, then try the hard drive in EFI mode first and if that doesn't work, try the old MBR mode.

---

