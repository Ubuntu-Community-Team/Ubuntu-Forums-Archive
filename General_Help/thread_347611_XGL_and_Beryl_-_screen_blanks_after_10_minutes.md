---
title: "XGL and Beryl - screen blanks after 10 minutes"
date: 2007-01-27
forum: General Help
---

### Post by stiankarlsen on 2007-01-27
I've been looking around the forums, and searching google, but I haven't come up with what I'm looking for.

The thing is that when using XGL/Beryl (Compiz for that matter), the screen blanks out after approx. 10 minutes, it even happens when playing fullscreen video.

The last time I had XGL installed, I remember finding something I added to my xorg.conf file, that would disable this "bug" or "screensaver" or whatever one can call it, but It's been a while, and i can't remeber what it was. (Something about ServerFlags).

I know this may not be much to go on, but does anyone know how to deal with this?

Thanks, Stian Karlsen.

---

### Post by aidanr on 2007-01-27
check your /etc/X11/xorg.conf for Option "DPMS" and either delete it or comment it out, and then restart x or reboot

---

### Post by stiankarlsen on 2007-02-06
no go

---

### Post by erugalatha on 2007-02-06
I've had a not dissimilar problem when I log out of a XGL/Beryl session my login screen is just black/blank.  

When I click near the prompt where the username usually goes there's a faint glow where the box for username usually is and when I click near the button in the left bottom corner to get the menu I can faintly see the menu appearing but can't see enough to see what I'm actually clicking on.  

I'm running it on an Alienware Area 51 m5500 is that info. is of use to anyone - might be same hardware as you.  Anyways when this happens I have to hard-reboot the machine as I don't know any other way to reboot when nothing appears onscreen.

---

