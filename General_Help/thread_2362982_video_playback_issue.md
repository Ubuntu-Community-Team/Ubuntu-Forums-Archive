---
title: "video playback issue"
date: 2017-06-04
forum: General Help
---

### Post by kmez619 on 2017-06-04
I recently have been using ubuntu mate lts 16.04 64 bit and think its great but there is one thing that is bothering me...when I play videos in any media player there is a slight frame line coming through every once in awhile like when u take a video of computer screen but not as bad... I have old hardware cpu is intel t7300 and gpu is nvidia 8400m g ..2 gb ram but the resources are not even close to being maxed out usually only at a 1/3 to half...ive played hd movies on even older machines than this in the past without any problems..Ive updated the drivers to nvidia ones and tried messing with different settings but dont kno what the problem is...other than saying my hardware is too old does anyone have any ideas or fixes on how to deal w this? thank you

---

### Post by mc4man on 2017-06-04
May be h tearing (no vsync). To get a better idea uploaded a small test file. If the bar breaks then you got tearing
```
wget https://0x0.st/E-U.mp4
```
(- will be dl'ed to home folder.

When the 8400m was current the nvidia driver settings had an option to enable vsync, I think that's gone now (can't tell as I've only optimus nvidia now & the 8400m isn't. 
Does the same occur if you use nouveau instead of nvidia drivers? I believe vsync was default enabled in nouveau some time ago.

If you get tearing in nvidia from test file & there is no direct option to enable vsync in nvidia-settings then search out, maybe there is an xorg.conf parameter you could use.

---

### Post by kmez619 on 2017-06-04
hell yea mc4man thanks alot... that was the problem..I looked in the nvidias x server settings and couldnt find anything so I searched and found this article [http://www.thelinuxrain.com/articles/got-tearing-with-proprietary-nvidia-try-this](http://www.thelinuxrain.com/articles/got-tearing-with-proprietary-nvidia-try-this) ....and it walked me through how to edit config files

---

### Post by kmez619 on 2017-06-04
basically you have to create the config file within nvidia x server in display configurations option and select save to x config file with current settings....than go and edit it and add [COLOR=#101010][FONT=Lato] { ForceFullCompositionPipeline = On }[/FONT][/COLOR]

---

