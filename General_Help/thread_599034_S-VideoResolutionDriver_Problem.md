---
title: "S-Video/Resolution/Driver Problem"
date: 2007-10-31
forum: General Help
---

### Post by Michael_TSM on 2007-10-31
**Solved, see below**

I recently hooked up a TV to my computer via the S-Video on my graphics card (GeForce FX 5200).
Unfortunately when I enable it as a second monitor or change my xorg.conf (using [this]("https://help.ubuntu.com/community/NvidiaTVOut") tutorial) several problems occur.

Initially while booting everything looks fine, but when I get past the Ubuntu loading screen I'm greeted with a black screen (with a cross as a cursor) and a dialog box that says: *"UBUNTU is running in low-graphics mode, Your screen and graphics cards could not be detected correctly. To use higher resolutions, visual effects or multiply screens, you have to configure the display for yourself."*
Whether I then configure the display or not, It still loads the resolution at 800x600 and uses the vesa-compatible (name may not be entirely accurate, vesa something anyway) graphics driver instead of the Nvidia nv driver and while the twin view works its not good for anything because my CRT monitor is stuck on 800x600 and I can't run any graphically intensive software because I'm stuck using the wrong driver.

Is it possible to get Twin View (Or any other 'view' for that matter) working with my CRT still at 1024 x 768 instead of 800 x 600, and Ubuntu using the Nvidia driver instead of the vesa-compatible driver?

**SOLVED:** Just go into the terminal and type in nvidia-settings and change it all from there instead on in the xorg.conf or Ubuntu's screen resolution program.

---

### Post by Michael_TSM on 2007-11-02
Does anyone have any ideas?

---

### Post by Michael_TSM on 2007-11-08
Solved,

You just need to open up nvidia settings and make the changes from there, as opposed to directly changing the xorg,conf or using Ubuntu's screen resolution program.

You accsess the Nvidia settings by going to the terminal and typing nvidia-settings

---

