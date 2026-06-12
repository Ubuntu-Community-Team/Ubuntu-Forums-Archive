---
title: "System fails to boot when hdd is connected"
date: 2015-04-07
forum: General Help
---

### Post by m-sheehan23457 on 2015-04-07
Greetings,

What I am trying to achieve is to be able to leave the hdd in semi-permanently and be able to reboot and it show up in pcmanfm with no problems.

I am running lubuntu 14.10, which was installed from a usb stick. Everything is fine until I attempt to boot while my hdd is plugged in at which point i get 'BOOTMNG IS MISSING CTR+ALT+DEL TO RESTART'. It happens consistently until I unplug the hdd and everything is fine again. This happens on all usb ports but one which will boot but not show the hdd until i unplug and reconnect it, so thats obviously no help.

I believe the system is trying to boot from the hdd as a priority when its plugged in, I've looked into grub customizer but i dont really see any reference to the hdd in there. I've had a long look around online and I can't get to the bottom of this.

Any ideas?

Edit: forgot to mention this also happens with usb flash drives

---

### Post by m-sheehan23457 on 2015-04-07
I found a solution on a pc forum, turns out this wasn't really an ubuntu problem but more to do with the hardware and its an easy fix (although it's apparently not so easy if you dont know what you're doing like me).

I changed the boot order using BIOS so that the hard disk was first and now it works great. To get to BIOS i held F10 during startup.

---

