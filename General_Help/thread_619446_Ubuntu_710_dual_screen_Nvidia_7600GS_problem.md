---
title: "Ubuntu 710 dual screen Nvidia 7600GS problem"
date: 2007-11-21
forum: General Help
---

### Post by errolgreer on 2007-11-21
[B]I have managed to triple boot XP Vista Ubuntu710. Works fine, but both screens show same data and mouse movements. In Windows, I can run different apps on each screen. I would like to do the same with 710. However, I tried to install the 7600 driver from the extra visual effects menu. This downloaded and intalled a driver which then caused chaos. I eventually had to reinstall Ubuntu from scratch as it even stopped the GRUB from allowing me to get back into Windows.

Any ideas ?

Errol
[/B]

---

### Post by Nunu on 2007-11-21
I got the 7600GS to, after I installed the OS I added the restricted driver and everything is working perfectly. 

Try install the driver called nvidia-glx-new from synaptic package manager then open a terminal and type in sudo -s and press enter. It will then prompt you for a password, after you logged on to root type in nvidia-settings this will bring up a configuration window similar to the nvidia control panel in windows

Where you can enable it to run two separate screens

---

### Post by Nunu on 2007-11-22
Sorry I forgot to mention to enable the restricted driver before you configure through the control panel

---

### Post by errolgreer on 2007-11-23
Thank you very much for your help !

I have it working and although I can set up say the spreadsheet on one screen and say firefox on the other, however, if I try to set up the word processor on the other screen, it goes to the screen which has the spreadsheet on it ! ie Openoffice apps have to be on the same screen. Have you noticed this ?

I am a complete beginner with Linux, but know Windows very well. Another thing, I enabled the special effects and see the waving windows. What other effects are available ? Like say the Vista "Flip 3D" for example ?

---

