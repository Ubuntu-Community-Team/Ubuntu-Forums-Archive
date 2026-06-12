---
title: "LCD optimization tweaks?"
date: 2007-03-01
forum: General Help
---

### Post by flummoxed on 2007-03-01
I just bought a 19" 1280x1024 LCD monitor. I'm looking for links to some optimization ideas/guides for making an LCD monitor more readable, and sharper in ubuntu.

Anyone have any suggestions?

---

### Post by fragos on 2007-03-01
Look at System-> Preferences-> Fonts.  Here you can set font renedering parameters and also select the default fonts you want the system to use.  System-> Preferences-> Screen Resolution is also a place to go.  Refresh can be set to 60 for all LCDs and is probably already set to that.  You may want to select 1280x1024 for your resolution.  If its not available there is more you'll need to do.  First the display driver for your video card determines which resolutions it will attempt to use.  The default is "vesa" and the max res is 1024.   Wheather or not you can select other resolutions depends on the graphics chip set on the mobo or on your video card.  The exact options depend on that chip set.

---

