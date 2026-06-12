---
title: "Setting screen resolution..."
date: 2006-10-16
forum: General Help
---

### Post by MartyLK on 2006-10-16
Hello to all.

I am new to ubuntu and am trying to figure out how to set the screen resolution to a higher level. It is 1024 X 768 right now and I'm wanting my usual 1280 X 1024.

Is this possible with LiveCD or do I need to install the OS?

My hardware:

Asus A7N8X-X MoBo
AMD AthlonXP 3200+ CPU
1 GB PC3200 RAM
EVGA Geforce 6800GT GPU w/256 MBs memory

I tried to install some nVidia drivers ...nVidia-glx... but it fails because they can't be found.

Also the AMD K7 files can't be found.

Help is greatly appreciated

---

### Post by John.Michael.Kane on 2006-10-16
The live/cd setup is for testing to make sure your hardware is supported.you need to install the OS to make any adjustments you may need.

---

### Post by neumeka on 2006-10-17
In order to add available resoltions (to the list in System->Preferences->Screen Resolution), you have to add them to your xorg.conf file.  because you cannot modify this file when using the live CD, you will have to do an install first.

---

