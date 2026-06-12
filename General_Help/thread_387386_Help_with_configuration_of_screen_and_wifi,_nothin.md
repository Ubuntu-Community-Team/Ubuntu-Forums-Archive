---
title: "Help with configuration of screen and wifi, nothing seems to work"
date: 2007-03-18
forum: General Help
---

### Post by rozojc on 2007-03-18
Hi,

I know this is not entirely correct, but I'm running Linux Mint, and since its based on Ubuntu I thought of asking you helpful guys for help over here, as I have two things that are not working at all with my new laptop:

1. Wifi (it's a broadcom)
2. Screen resolution

I tried blacklisting the broadcom module that mint uses (which does not work) and then using the one my laptop uses for windows (Vista, cause there's no driver available for XP) through ndiswrapper, but it doesn't seem to work... And I did it exactly as I've done it before... just ndiswrapper -i whatever.inf, then ndiswrapper m , and finally modprobe ndiswrapper... I get no mistakes at all, no warnings or similar, but if I do an iwconfig, the freaking wlan0 simply does not appear as if it didn't exist!!!! IDEAS please???

2. Screen resolution: My screen should work at 1280 x 800, but Mint recognizes it at 1024 x 768. I manually edited xorg.conf, and (since I was unable to make it work) changed ALL instances of resolutions (yes, ALL of them, including 800x600 , etc) for 1280x800, and still each time I log in it works at 1024x768... How can I override that resolution if its not through xorg.conf???

Any help will really be appreciated!! thanks

---

