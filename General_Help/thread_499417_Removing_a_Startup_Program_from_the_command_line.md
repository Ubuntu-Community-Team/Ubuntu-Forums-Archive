---
title: "Removing a Startup Program from the command line"
date: 2007-07-12
forum: General Help
---

### Post by SaberSHO on 2007-07-12
Hi all,

Im relativly new to the Ubuntu world and wanted to play with Fusion-Compiz. I was having trouble getting window decorations and was told that doing compiz --replace would fix it. It did, but it was running in the terminal window and as soon as I closed the window, the window decorations would disappaear. To fix this, i decided to try and make it a Startup Program under System - > Preferences -> Sessions. I added the command compiz --replace and named it compiz window fix. 
However, this seems to have been a dumb idea, since X no longer starts at all. I would like to be able to remove this Startup Program using the command line(since I cant boot X), but I am not sure where these Startup Program settings are found. I have tried searching in rc.local as well as xinit.conf (or something like that). Any tips would be appreciated. TIA

-SaberSHO

---

### Post by sisco311 on 2007-07-12
```
rm /home/**your_user_name**/.config/autostart/*compizXXX.desktop*
```replace **your_user_name** with your user name and *compizXXX.desktop* with the proper file name

---

