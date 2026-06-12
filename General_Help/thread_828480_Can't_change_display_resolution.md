---
title: "Can't change display resolution"
date: 2008-06-13
forum: General Help
---

### Post by Osillius on 2008-06-13
8.04 Hardy Heron
Using an Nvidia FX5900 with a Dell Ultrascan P780

I can't change the resolution to a reasonable level.
Using the default vesa driver I can get 800x600, 640x480, and 320x240
Using the Nvidia driver from the EnvyNG package I get 640x480 and 320x240
Using the latest nvidia driver from their website (175.14.05) I get 640x480 and 320x240

I've tried manually editing the xorg.conf for the modes but no luck. I used Nvidias xconfig utility, also with no luck. I tried the Option "UseEDID" "False" (on both the Screen and Monitor sections, individually and together just to be thorough)also with no change.

From there I got a little creative, I ran the EnvyNG utility after installing the latest nvidia drivers(without removing them, envyng installed 169.??) and the gui started with a dialogue that the display was messed up and allowed me to manually set the monitor and graphics driver. 

I checked the xorg.conf(after manually setting monitor and graphics drivers) and noticed a lot more detail in the modes subsection for the monitor and screen sections.
Still no change in the available resolutions through 
System > Pref. > Screen Resolution

This is the first box I've ever installed any version of linux on, and this driver was the first thing I went for when it booted up the first time....and I'm fresh out of ideas.

Anyone have any idea if I'm missing some detail or how to fix this?

Thanks in advance

---

### Post by Osillius on 2008-06-13
UPDATE

Ran gksudo displayconfig-gtk, set everything and logged out and back in.
Works great once the GUI starts but now my login screen only shows the top left 1/4 of the screen(roughly)

one problem at a time =)

---

