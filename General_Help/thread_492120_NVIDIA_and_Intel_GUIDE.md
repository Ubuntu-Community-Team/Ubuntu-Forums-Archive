---
title: "NVIDIA and Intel GUIDE"
date: 2007-07-04
forum: General Help
---

### Post by Dark Ares on 2007-07-04
I've been having many problems using my Geforce FX 5500 graphics card on my pc. I have a Dell Dimension 2300 that doesn't allow disabling of the integrated Intel Graphics card. So any time I insert the Nvidia card I get kernel panic at startup. Looking on the internet I didn't find guides exactly for my Ubuntu Version [7.04], so I decided to help future people with my same problems. Fixing the problem is actually very easy.
I only had to install 2 programs [that I will use in this guide], Boot-Up Manager and Envy. The first program is necessary to disable gdm from autostarting, enabling us to start the pc with a text base console; the second one will install the nvidia drivers and also configure xorg for us. You can get Envy [here]("http://www.albertomilone.com/nvidia_scripts1.html"). 
So start your pc with the nvidia card not inserted. 
Start BUM and disable GDM, then press "Apply" and then NO, because we need to do some little blacklisting before.
Type from the console
> sudo nano /etc/modprobe.d/blacklist
and add the following lines at the bottom
> blacklist agpgart
blacklist intel-agp
Then exit saving the file.
Turn your pc off and insert the nvidia card. If this was done without blacklisting those modules we would of got kernel panic, but theoretically now we should be able to get to a text login. Login and then type the following to start Envy in text mode:
> sudo envy -t
This program will do all the driver installing for you and after a couple of minutes it will ask you if you want it to configure xorg, after that it will ask to start x. Answer yes to these questions and you should see gnome loading.
Reload Bum and reenable gdm at startup.
Next launch NVIDIA setting under the applications menu and tweak the screen setting as desired.
The graphics card should be now fully installed. If you think there is something wrong or simply need a little help understanding, don't hesitate and ask.
Ciao

---

### Post by Robin T Cox on 2007-07-04
See also:

[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by fragos on 2007-07-04
Sounds like installing the Nvidia card didn't automatically disable your on board video.  Boot you system with the Del key down to start the BIOS.  Check to see if there is a BIOS parameter for disabling the on board video.

---

### Post by ubuntujonez on 2007-07-05
I think I had similar problems with my Dell Dimension 4600. (intel on board + nvidia). Thanks for the links!

---

