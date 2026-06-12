---
title: "apple cinema display w/ Ubuntu"
date: 2007-01-09
forum: General Help
---

### Post by mas07 on 2007-01-09
Hello,

I just installed 6.10 on powerpc. Everything went very smoothly. I have a 20" Apple cinema display and I had to change the xorg.conf a little so i would have the optimal resolution for my screen (1680x1050). Before I changed xorg.conf the only resolution available was something like 800x600. Basically i had Ubuntu desktop in the middle of the screen. Not very nice!!
I read a lot on different forums to find out that many people had the same issues. The only problem i have now I think that  the refresh rate is too slow. Basically every time i drag a window or open an application, I see a trail. Even when i shut down and the screen changes color I actually see the screen drawing from top to bottom. Now I really think thats something to do with the setting in the xorg.conf. It has to be better than that. I attached xorg.conf. I can provide Xorg.0.log if needed. I found a site where it specified the horizontal and vertical freq, and I assumed they were right right because when i entered them in the xorg.conf it worked. However Apple has no idea what those are!!!! I'm running Ubuntu on a G4 mac and I wiped the OSX completely. 
Any help would be appreciated. 

thanks,
mas

---

### Post by TheJackofClubs on 2007-01-09
try running "sudo dpkg-reconfigure xserver-xorg" (without quotes) in a terminal to resetup you xorg.conf. it gives alot of options for this stuff and i end up running it on almost all my ubuntu installations but it helps optimize it alot so i say give it a try. make sure to select your resolutions since it it only selects a few default ones.

---

