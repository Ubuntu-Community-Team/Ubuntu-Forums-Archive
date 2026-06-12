---
title: "Black Screen"
date: 2008-04-05
forum: General Help
---

### Post by dragon3700 on 2008-04-05
I have just installed Ubuntu Hardy using Wubi on my Windows XP Home Dell. On first reboot, the initial install for Ubuntu went fine, and then I had to reboot again. I booted Ubuntu, and after the loading bar for start-up, I get a black screen. I searched the forums and found people with the same problem, but I don't understand the solution. I have an Nvidia GeForce 6150 LE graphics card. Please help!:confused:

---

### Post by ago on 2008-04-05
Press ctrl+alt+del
Login
Run the following command:
Sudo dpkg-reconfigure xserver-xorg

Select vesa and leave the other options at default
Reboot

---

