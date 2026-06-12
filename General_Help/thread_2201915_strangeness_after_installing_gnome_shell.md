---
title: "strangeness after installing gnome shell"
date: 2014-01-26
forum: General Help
---

### Post by Alistair_Danhieux on 2014-01-26
Hi all,

Just downgraded back to 12.04 LTS on a fresh install with / on a separate partition from /home. I prefer Gnome classic to Unity so I installed it through the Software centre. Various issues then arose:

1. I no longer get the snazzy login screen that came along more or less at the same time as unity. I get its predecessor...

2. I now get an odd Debian grub screen (grub 1.99) with stars and a bit of planet earth on it.

3. shutdown and restart just get stuck at the ubuntu screen and hang when I choose 3.8.0-35-generic and 3.8.0-29-generic (I have to hold the power button to get it to turn off), but they work fine when I choose 3.2.0-58-generic-pae.

I then read that it is not a great idea to install gnome shell through the SC so I removed it and did a purge (as per [http://askubuntu.com/questions/65200/remove-gnome-shell-completely-after-installing-it](http://askubuntu.com/questions/65200/remove-gnome-shell-completely-after-installing-it) (scroll down to "remove all packages")). That changed nothing. I ran sudo update-grub and that changed nothing. I then installed gnome shell through the terminal which also changed nothing...

Does anyone have any ideas?

Thanks for your time.

---

### Post by ajgreeny on 2014-01-26
Gnome shell is not the same as classic gnome, as far as I'm aware, though I admit that I don't use either.

I think you need to install gnome-panel, plus its dependencies for classic gnome.

I haven't looked for a long time now but have a good look at 
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by Alistair_Danhieux on 2014-01-27
Hi AJ,

Thanks for that. It looks like what I should have gone with, If I end up doing a fresh install it's what I will do.

Right now though I'd like to try to try to get things running smoothly without going through a new install. The biggest problem at the moment is the fact thet it just hangs on shutdown unless I use the oldest version of Linux kernal available to me. It means going throuh "advanced options" each time at startup... I'm starting to think that it may be to do with my hardware getting a bit old (2006-7) as this is not the first time it has happened (after upgrade).

I'll wait to see if anyone can help and I'll probably end up reinstalling and hoping for the best.

Many thanks anyway.

---

