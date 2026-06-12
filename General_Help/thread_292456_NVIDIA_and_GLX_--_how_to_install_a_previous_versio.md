---
title: "NVIDIA and GLX -- how to install a previous version?"
date: 2006-11-03
forum: General Help
---

### Post by WinterWeaver on 2006-11-03
Hi hi ^.^

ok... i've had the nvidia-glx v.8774 drivers installed. and I was quite happy with everything, until I installed cedega and tried to run Guildwars. Guildwars runs beautifully, with no lag at all, nice smooth good looking graphics and reflectsions.

I do however have one major problem... FONTS & Icons are all screwed up into oblivion ... T_T ...

well after a month of browsing forums and trying everything that everyone mentioned, it basically came down to 2 last options for me to try...

1 - upgrade my graphics card
or
2 - install v.7148 (nvidia driver)

well 2 is obviously the cheaper option, so I downloaded v7 from teh nvidia site, removed nvidia-glx and the like, did the whole init.d/gdm stop thing, and proceeded with the install.

sudo sh "very long nvidia installer name"

but I'm having troubles... *sigh

can anyone help me?
X starts, but now I don't have any glx, hence glxgears don't work, no opengl and no Guildwars at all ... :(

any help and/or suggestions will be greatly appreciated.

ta

---

### Post by WinterWeaver on 2006-11-03
Ok... I decided to give up on this.... but now I have a new problem...

I uninstalled mostly everything that I could think of.
Reinstalled the up-to-date version of nvidia-glx

after it was installed, I ran:
```
sudo nvidia-glx-config enable
```

it did all it's wee things, after which I ammended the xorg.conf with all the rederaccel and twinview options....

still no glx ... :(

](*,) 

anyone know what's going on here ?

---

### Post by WinterWeaver on 2006-11-03
Saved by teh man and his wonderful howto!!!!

[http://www.ubuntuforums.org/showthread.php?t=281823](http://www.ubuntuforums.org/showthread.php?t=281823)

^.^

---

