---
title: "Nvidia 7600 GS 512MB not compatible with Ubuntu"
date: 2007-05-22
forum: General Help
---

### Post by newuser19 on 2007-05-22
I tried a lot of things. I have BFG Nvidia 7600 GS with 512 MB.

Can't get it to work with Ubuntu 7.04. Only uses NV driver. I did the apt-get to install nvidia-glx. Tried differnt versions as well. Everything installed fine. Enabled the driver and created a new xorg.conf. Great. Restarted the machine and X won't start!

"No screens found"  

Reformatted and re-installed about 4 times - trying different methods.  The results are all the same: No screens found.

Went back and installed ubuntu 6.10.  Same thing happens: No screens found.

I swear, this card is not compatible with Ubuntu or I'm doing something terribly wrong.  I'm a new attempted linux user.

---

### Post by jrusso2 on 2007-05-22
If your using the restricted drivers installer check this 

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106649](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106649)

Make sure the right version is being installed

---

### Post by Brynster on 2007-05-22
i had the same issue which i fixed yous TSELIOT's marvelous Envy script. follow these instructions:-


[HTML]http://www.albertomilone.com/nvidia_scripts1.html[/HTML]

Got the Nvidia drivers in and working beautifully.

---

