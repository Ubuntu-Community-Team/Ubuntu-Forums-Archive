---
title: "Mousegrab problem with X11?"
date: 2013-06-15
forum: General Help
---

### Post by d4rin on 2013-06-15
I've just installed Ubuntu and I am having some "Mousegrab" Problems, At least that's what I've read about it.

I downloaded a game-server-browser program, And Sometimes when I am clicking on different servers in the program it will just freeze up. I cannot click on anything but I can still move the mouse around. I am forced to log out and log back in.

It also happens when I run a game in a different X server, I can alt+enter and minimize the game...But sometimes it won't maxamize or I can't click on anything at all or exit the game.

Is there a fix for this? It's pretty annoying.

---

### Post by searchfgold6789 on 2013-06-16
Which graphics card do you have, and are you using proprietary drivers?
And what is the name of the program?

---

### Post by d4rin on 2013-06-16
I am using a Laptop, ATI Radeon HD6320.

The program is called XQF Game Server Browser.

*-display               
       description: VGA compatible controller
       product: Wrestler [Radeon HD 6320]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:42 memory:c0000000-cfffffff ioport:f000(size=256) memory:f

[Radeon HD 6320]
    Subsystem: ASUSTeK Computer Inc. Device 104c
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates, radeon

Hmmm, Shows no proprietary drivers are in use. But there is an post-release update of a proprietary driver activated but not in use.

I installed a proprietary driver but it is not in use, And I am not sure how to enable it.

It may be because the card for my Laptop is not supported?

EDIT: Ok...I've actually found the correct drivers on the ATI website. That game browser program still crashes the same way, But when I alt+tab in my game it doesn't seem to crash anymore.

I think that XQF program is just buggy...And it's very old.

---

### Post by searchfgold6789 on 2013-06-18
Yes, I wouldn't expect a game that old to play well with modern software, especially modern graphics software. Driver features change and out-of-date programs become unable to handle them.
You could try something like using an older graphics card driver. I checked everywhere online, but couldn't find any info OR drivers for your card - maybe you would have better luck with that.

---

