---
title: "PS2 failure in gutsy (XP affected now too)"
date: 2007-10-04
forum: General Help
---

### Post by Vaphell on 2007-10-04
i have really nasty problem :(

i had XP SP2 on my PC and decided to slowly migrate to ubuntu. I use 6.10 in my work but I wanted to see what is in gutsy so i dloaded beta iso. I thought first ubuntu install would be test one anyway so no stress.

Live CD didn't find any PS2 hardware: logitech basic models of mouse and keyboard were frozen/bricked. I thought that it's some glitch and installed gutsy beta anyway. I moved mouse to USB and I filled text fields using clickable char table. That was a bad idea :[

result:
keyboard always freezes - just after selecting OS in GRUB, no matter what - both xp and ubuntu are affected. Spamming capslock stops changing indicator state.
I dloaded some small linux distro live cd and checked that keyboard still works in other OS.

My only hope was that removing grub by fdisk /mbr somehow would fix the problem. After some hassle i managed to do that - booting from cd was not affected because keyboard dies later, during hdd booting. Unfortunately booting straight to XP still bricks my keyboard. 

So now i am without basic input device unable to to log in to any of OSes, i can just look at pretty login screens and that's about it. My pc is only useful as a file server as remote loging in still works :/

Any idea what went wrong and why PS2 ports hang after ubuntu install even after removing grub? :confused: And more important: how to fix it ffs? :mad:

some pieces of my gear: amd64 3000+, mobo ga-k8nf9 (nF4), 512bm ram, gf6200, 2 sata drives (seagate x2)

---

### Post by atlfalcons866 on 2007-10-04
did you try using another ps2 keyboard and mouse?

---

### Post by Vaphell on 2007-10-04
i havent tried another mouse, at least mouse works in usb so its not that critical. Another ps2 keyboard hangs too. DamnSmallLinux live cd works ok, keyboard is usable. PS2 ports seem to die in the 1st second of hdd booting - ubuntu and XP.

This problem really crippled my enthusiasm toward ubuntu and linux in general :[
Linux installation breaking other inastalled OS is a grave sin, broken PS2 support is just lame :/

---

