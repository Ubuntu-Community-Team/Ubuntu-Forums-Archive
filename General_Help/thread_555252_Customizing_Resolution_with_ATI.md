---
title: "Customizing Resolution with ATI"
date: 2007-09-19
forum: General Help
---

### Post by bendystraw on 2007-09-19
Ok so i just figured out how to get a bigger resolution with Feisty Fawn for the people that need help in getting a bigger resolution with a ATI card...

Step 1) Go to System > Administration > Restricted Drivers Manager
Enable the ATI driver if it is not already enabled (restart is required)

Step 2) Go Applications > Accessories > Terminal 
Type  sudo dpkg-reconfigure -phigh xserver-xorg
Type in your Pass (note that it is not echoed so just type it in and press enter)

Step 3) use the Arrow keys to find ATI and press Enter

Step 4) Use the arrow keys again to find the resolution you want that you think your monitor will support and hit the space bar

Step 5) when you select all the resolutions you want that you think your monitor will be able to do hit Enter

Step 6) Go System > Preferences > Screen Resolution

Step 7) Select it and press Apply and then Keep Setting


Hopefully that works for you i know i searched long for it

:popcorn:

---

### Post by NeoDaVe on 2007-09-20
Just! Thanks :D =D>

---

### Post by bendystraw on 2007-09-21
> **NeoDaVe said:**
> Just! Thanks :D =D>

Glad it could help, i cant quite use the terminal amazingly yet but im gonna try to help out the community by providing my guides and troubleshooters =] i know alot of other guides are way out of date or you finnaly find the guide you need and they provide a link that dosnt work, hopefully i can help more people =]\\:D/

---

