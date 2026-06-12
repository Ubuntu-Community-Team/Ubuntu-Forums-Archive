---
title: "Interesting display issue."
date: 2016-08-08
forum: General Help
---

### Post by name14 on 2016-08-08
I had a Ubuntu (14.04) computer that I was using with a Emerson LED screen, everything was working fine and image was displayed on screen. But my computer would lag when opening anything with Ubuntu so, in hearing that it was more lightweight, I decided to to try out Lubuntu. 

Because my computer didn't currently have any internet connection I had to move it to where the router in my house was and use a Ethernet cable, because I had to be wired in I had to use another screen I had which was a LED Asus (this is very important.)

Everything went well, I installed Lubuntu, I didn't get the "black screen of death," I was able to upgrade it to 16.04, and set everything up the way I wanted (deleted some programs it came with). After that I brought it back to the Emerson screen and wired it up, when I turned it on and, after the BIOs display and grub, I was greeted by a completely black screen that never went away.
So, essentially, the computer displays on my Asus screen but not the Emerson screen, which is where I need it.

I'm not unfamiliar with Ubuntu Black screening, but am not well versed in it to fix it on my own, so I looked for a solution online,
I got into grub and added "nomodeset" before, after, and replaced "quiet splash" with.
I permanently added "nomodeset" in grub through terminal just in case it  was always reverting back whenever I typed it in at start up.
I looked up the graphics card in my machine and tried to update/install the Intel packages, but it was already installed.
I tried using a Intel propitiatory additional driver that I found on my computer.
I attempted to "try Lubuntu (14.04) without installing" from the flash drive I had. (Also with "nomodeset")

I feel as though I've tried everything but I can't figure out why It displays on one monitor but not the other, and nothing is working.
I would appreciate any help. 


Hardware info:
[https://www.amazon.com/Intel-Fanless-Mini-ITX-D2500CCE-PD12TI/dp/B008KB5YCK](https://www.amazon.com/Intel-Fanless-Mini-ITX-D2500CCE-PD12TI/dp/B008KB5YCK)
"Intel Atom D2500 Dual LAN, Dual COM Fanless Mini-ITX PC, D2500CCE, 2GB, T3410, Mitac PD12TI
 Dual Intel 82574L Gigabit Ethernet Ethernet ports; Dual Serial COM ports
 Embedded Intel® AtomTM D2500 1.86GHz dual-core CPU; Silent, Fan-less Solution
 Supports 1 x 2.5" SATA HDD or SSD
 Morex T3410 Fan-less Enclosure with VESA mounting bracket
 Motherboard: Mitac PD12TI CC Mini-ITX Motherboard"

Asus LCD screen
 Emerson LCD screen

---

