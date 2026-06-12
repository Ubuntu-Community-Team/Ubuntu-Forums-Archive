---
title: "No visual after graphics installation"
date: 2013-11-12
forum: General Help
---

### Post by Nakira89 on 2013-11-12
Hi all, i tried installing some AMD graphics drivers for my Radeon HD graphics, however after the installation, i can no longer view anything, i can see grub on start up but ubuntu doesnt work in normal or recovery mode with fail safe graphics mode on, i have no idea what i did wrong, but obviously something aint right here. 

Any help would be great, thanks in advance. :)

p.s. (It was this driver i installed, and used --force to overwrite the current fglrx iirc?) [http://support.amd.com/en-us/download/desktop?os=Linux+x86](http://support.amd.com/en-us/download/desktop?os=Linux+x86)

---

### Post by QIII on 2013-11-12
Hello!

Could you tell us your hardware specifications and which version of Ubuntu you are using?

Thanks.

---

### Post by Nakira89 on 2013-11-13
Ubuntu 12.04

HP Envy M6 1302sa

and the graphics card is [FONT=HPSimplified]AMD Radeon HD 8650G/7670M Dual GPU (2 GB DDR3 dedicated)

Thanks in advance[/FONT]

---

### Post by Nakira89 on 2013-11-15
Anybody have any idea how i can go about this?

---

### Post by QIII on 2013-11-15
Did you execute the .run file directly, or did you make a .deb file from it?

---

### Post by Nakira89 on 2013-11-16
Yeah i ran it straight from the .run file, was this a mistake? Everything apperared to install correctly. and was working until i rebooted my machine

---

### Post by Nakira89 on 2013-11-18
is there nothing i can do? I really dont fancy doing a full re install as this seems over the top for a graphics issue. :(

---

### Post by Mark Phelps on 2013-11-19
> is there nothing i can do?

Sorry to tell you this -- but probably not.

You have one of the new dual-graphics notebooks, for which the drivers are supplied by the notebook manufacturer, NOT AMD.

Forcing the installation of AMD drivers is most likely going to corrupt the display -- as the drivers at their site are not designed to work on your notebook.

And, since HP does not generally supply Linux drivers, then you will have to get by with the default Radeon drivers that were installed during setup.

---

