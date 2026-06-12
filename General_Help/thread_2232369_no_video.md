---
title: "no video"
date: 2014-07-01
forum: General Help
---

### Post by Dave_Rose on 2014-07-01
I just upgraded to Ubuntu 14.04. Since then I've had problems with the screens freezing, losing color. Today I decided to look into it a bit. I found out I should do a little tweaking. I'm not a real techie but I figured I'd try some stuff. I found a driver for my ati card, installed it and rebooted. After that I had no video. I managed to get into the setup screen. I saw a line for the video adapter I believe. One said pci the other said pci-e the other said on board. I tried on board and now I can't even get to the set up screen. I have the cd with ubuntu 12.10 on it but am unable to boot from that. 
Any advice would be greatly appreciated. 
Thanks in advance

---

### Post by Mark Phelps on 2014-07-01
Your BIOS setup screen indicated three video options, the onboard is for the video chip built into the PC; the others are for add-on cards.  If you have BOTH onboard video and an add-on ATI/AMD video card, it's possible you have Hybrid graphics -- and the drivers from the AMD site don't work for those.

If you were using the add-on card, you were already running the default Radeon drivers and should NOT have forced the installation of other drivers.

Also, with both onboard graphics and a video card, there would be TWO video jacks on your PC -- one for each of those.  You need to have the screen connected to the jack for the video chipset you are using.  If you had it connected to the add-on card and switch the BIOS to onboard, you need to switch the monitor cable to the onboard jack as well.

---

