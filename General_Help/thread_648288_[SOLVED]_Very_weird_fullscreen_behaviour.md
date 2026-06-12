---
title: "[SOLVED] Very weird fullscreen behaviour"
date: 2007-12-23
forum: General Help
---

### Post by zarqoon on 2007-12-23
I just installed Gutsy some days ago and i noticed something weird.
Every time i play a game in fullscreen every few minutes the game switches from fullscreen to window mode and approx. 2 sec later back to fullscreen.
I noticed it with globulation2, pathological, singularity and some others. All from the ubuntu repository.
Everything else works fine. Even Xgl and compiz-fusion.

Hardware:
Amd64 Venice 2.2ghz
Asus A8N-E
ATI X800GTO (driver fglrx)

---

### Post by icechen1 on 2007-12-23
Do you have compiz (desktop effects) enabled?try disabling it because it causes some problem with some games.

---

### Post by dlegend on 2007-12-23
Try going to System > Preferences > Advanced Desktop Effects Settings and find "Workarounds" under the Utility section. Check "Legacy Fullscreen Support" -- if it's already checked, try unchecking it. Not sure if this will work but it's worth a shot.

---

### Post by zarqoon on 2007-12-23
Already did turn off xgl and compiz does not make much difference. Globulation runs better without it but the fullscreen problem remains. Its not that much of a problem but very annoying.

Unchecked the legacy fullscreen support. Didnt change anything as far as i can see. Compiz is disabled though.

---

### Post by zarqoon on 2007-12-23
I just played again for half an hour and its not just very annoying its extremly annoying.
Does noone have any more ideas?

---

### Post by nzadLithium on 2007-12-23
a not very helpful idea. get a nvidia card. I have never had any issues with nvidia cards (cept when i installed to versoins of the nvidia drivers at once :S) 

my ati card in my other linux machine has always been a pain in the ***. the latest driver from ati/amd works alot nicer! i get about 30 fps average on quake based games now compared to the 4-10 fps from previous drivers. cant wait for the next release! try installing the latest fglrx driver from source.

follow this to install from binary 'blob'
[http://wiki.cchtml.com/index.php/Ubu...river_Manually](http://wiki.cchtml.com/index.php/Ubu...river_Manually)

if you get opengl errors (i did)
then run this
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

---

### Post by zarqoon on 2007-12-23
I've some other information on my problem.
It seems to occur fairly regular. Every 10 minutes to be exact. I checked the crontabs and they seem to be empty/nonexistent. I dont think its a graphics driver problem because its so regular and everything else works fine graphics wise but i've no idea what it could be otherwise. It seems to be not related to specific games too. Happens with everything. Even dosbox with Ascendancy.

---

### Post by zarqoon on 2007-12-24
It seems to have been the screensaver that activated every 10 minutes kicking me back to the desktop. I changed the wait to 1 min and it happened every 1 minute i disabled it and it does not happen anymore.
So my problem now is how do i get gnome to notice that i am moving my mouse while i am in fullscreen mode? I would like to let the screensaver switched on but if it activates all the time while iam playing ... you see the problem

---

### Post by nzadLithium on 2007-12-24
lol thats really weird. googled it and found this thread
[http://ubuntuforums.org/showthread.php?p=1524621#post1524621](http://ubuntuforums.org/showthread.php?p=1524621#post1524621)

it says to modify the ServerFlags section of your xorg so it looks like this:

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection

to get to ur xorg (just in case you dont know :D) copy and paste that into a terminal

gksudo gedit /etc/X11/xorg.conf

edit those lines and hopefully it will fix :S

---

