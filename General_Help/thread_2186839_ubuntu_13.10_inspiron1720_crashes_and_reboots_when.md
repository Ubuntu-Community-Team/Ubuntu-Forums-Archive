---
title: "ubuntu 13.10 inspiron1720 crashes and reboots when watching videos in fullscreen"
date: 2013-11-09
forum: General Help
---

### Post by slippycurb on 2013-11-09
hey gals n guys,
my friends laptop has been crashing when watching videos (in fullscreen only) from youtube (or 4od, rte player etc) in google chrome or firefox, it doesnt happen when watching vids in vlc so im kind of confused,,,,,the laptop restarts completly.
ive already posted an lshw and dmesg output  here [http://ubuntuforums.org/showthread.php?t=2186738&](http://ubuntuforums.org/showthread.php?t=2186738&)
this has only started to happen since the upgrade from 13.04.....
does anybody have any clues? should i reinstall 13.04 (but i dont want to as everything else seems grand)

---

### Post by prshah on 2013-11-09
Ubuntu has an open-source replacement for Adobe Flash technology called gnash. However, there may some compatibility and / or stability problems with this at times.

You can check if you are using the gnash player by opening FireFox, then typing the below link into the address bar:```
about:plugins
```

If you would like to replace gnash with the proprietory flash player plugin, close firefox and any other browsers, then open a terminal (Dash-Terminal) and give the command ```
sudo apt-get install gnash- flashplugin-installer
``` and follow instructions.

Please post back with results or if you have any questions, comments and/or suggestions.

---

### Post by slippycurb on 2013-11-12
Hey thanks for getting back, I think you are right with it being flash problems, and it stems from the fact that I had to do a hack to get those video players to work when using 13.4...(HAL wasn't installed by default if i remember correctly back then)...when i checked about:plugins I was actually using shockwaves flash plugin, i tried updating to the newest flash but it did not help, so i tried removing flash and installing gnash, which didn't help either...I feel (but its definitely not expert opinion) that something somewhere was being left behind and just messing something up.......
Last night I just decided that it would be best if reinstalled completely fresh to 13.10 and I don't think my friend has had any problems as of yet, and the backup of his files was relatively easy......
I haven't actually checked if 4od or the rte player are working, but I left a youtube video on that lasted for over an hour (whence before the laptop would have normally crashed before finishing) and it seemed grand.
Thanks very much for your assistance.
Tris

---

