---
title: "I killed my X by plug in my laptop into an external Monitor?"
date: 2007-01-29
forum: General Help
---

### Post by Gamebeavis on 2007-01-29
Morning all,

Ok, last night I plugged my Dell e1505 laptop into my external monitor (TV) hit the button that cycles my monitor selection and then things went bad. It did display the correct image on the screen, however it was only in 640x480. So I figured that my laptop just wouldnt do the 1280x720 required for the TV (my laptop has a native of 1280x800). So I switched back to the laptop screen which was then in 640x480. I restarted X (ctrl, alt, backspace), and then it was gone, and all I could access was terminal windows. So I logged in, loaded "xorg.conf" into vi and had a look. Apparently just plugging the TV into my laptop changed my config file to only support 640x480 at 16bit with NO other options?? What the *&$&%?? So I rebooted thinking it would "fix" the problem. NO dice. So I plugged the laptop back into the TV, wallah I have picture at 640x480 again, however at this point I also noticed I no longer have wifi? 

I tried rebuilding my xorg.conf with dpkg-reconfigure, but wasnt overly sure of some of the selections I made. I did get my screen to come back, but im not sure if all the settings were done correctly, and I also still do not have my wifi... Also im a little scared of possibly having selected the wrong vertical and horizontal sync rates, and dont want to burn out my monitor.

I guess the real question is this. In ubuntu is there a way to auto rebuild the xorg.conf, or do a complete hardware detect all over again?? This way ubuntu makes the correct choices for my hardware?? Also, what the hell happened when I plugged it into my external monitor?

Thanx.

---

### Post by renzokuken on 2007-01-29
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Gamebeavis on 2007-01-29
Thank u, but I tried that. Im not overly sure of which selections to make during the process when its asking me to select bus speeds and sync rates etc. Also, it didnt mention anything about my wifi selections. Is there a way to rebuild the xorg automatically as well as "redo" the hardware detection?

---

### Post by gwpritch on 2007-01-29
As long as you didn't change out any other hardware than the monitor (ie video card, mouse) the only thing you should have to change in xorg.conf would be the  Monitor settings, which you can do manually with an editor and root privilages.  Google around for  HorizSync and VertRefresh Specs for your monitor. The wifi problem is an entirely separate issue from your X configuration. Unless you had static problems and fried something when you changed monitors, its probably just a coincidence that you lost your connection.

---

### Post by renzokuken on 2007-01-29
with the above command you can usually just accept the defaults and just change the driver and resolutions as needed.

as for another way, sorry no idea. i'm sure there is but i dont know it.

---

### Post by kpkeerthi on 2007-01-29
Boot with live CD. Make a copy of live xorg.conf on to an USB flash drive. Then boot ubuntu from hard disk and diligently compare and merge the two files.

---

