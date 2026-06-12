---
title: "Fullscreen=&quot;Mode Not Supported&quot;"
date: 2008-06-01
forum: General Help
---

### Post by gosharik12 on 2008-06-01
Just as the title says, anything that goes into full screen whether it's openarena to childsplay probably movieplayer too. It all goes to a blank screen and sometimes the screen is on but says mode not supported, I'm guessing either the refresh rate or the resolution does not correspond to the monitor, but I honestly don't know. I already reinstalled Ubuntu once since whatever program I opened had a blank screen and indefinitely crashed Ubuntu causing some files to be corrupt. Because when I restarted it it would cycle a black screen and 4-5 lines that said [ok] at the end. Either way I'm just trying to find out if I just need to update the video card drivers or change some setup files. Anything will help.

Thanks in Advance,
 Gary

BTW Specs- P4 2.80Ghz, Dell 4600 Mobo, Nvidia 5200fx, 1gb ram, sound blaster 24-bit(not in use)

---

### Post by gosharik12 on 2008-06-01
Bump

---

### Post by Capt_Scribble on 2010-08-23
Similar (if not the same) problem here. Any program, either 2D or 3D, that tries to go full screen is out of range. I can get back by toggling full screen mode by pressing alt-enter. And all the programs run fine in windowed mode, just not full screen. I did not have this problem before with Ubuntu 9. I tried using different nvidia drivers but no change. Any help or suggestions would be appreciated!

---

### Post by Capt_Scribble on 2010-08-26
I unintentionally fixed it. :)

Something else messed up my nvidia drivers so I uninstalled and purged all of them. Then I added x-swat ppa to the repositories and installed the nvidia-current drivers. Now I can run programs full screen. I still don't know what difference there was between Ubuntu 9 and 10 if I was using the same nvidia drivers though.

---

