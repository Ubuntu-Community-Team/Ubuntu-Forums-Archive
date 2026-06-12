---
title: "Blackscreen after splash without nomodeset - also means I can't get full resolution"
date: 2018-07-06
forum: General Help
---

### Post by muserdekal on 2018-07-06
Hi there,

I can't get past the splash screen unless I have nomodeset in my grub config. However, this means that I can't get full 4k resolution on my monitor. Can someone help? I have a Dell PC with an nvidia P600 card.

If I install the drivers I get a blackscreen after splash even with nomodeset. The only way to recover is by purging everything nvidia.

Without nomodeset, I get no signal from the PC to the monitor and the monitor switches off. It does not come back on even after several minutes (tested up to 30 mins).

I'm running Ubuntu 18.04, clean install. Drivers tried - nvidia 390, 396. 

I've tried 

sudo ubuntu-drivers autoinstall

as well as

sudo apt install nvidia-390

---

### Post by Autodave on 2018-07-06
Please give us some info. What driver are you/have you tried using? Where did you get the driver from?  What Linux are you running? Was this a clean install or did you upgrade from a previous version?

---

### Post by muserdekal on 2018-07-06
Updated post. Thanks!

---

