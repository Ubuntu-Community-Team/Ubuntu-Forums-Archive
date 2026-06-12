---
title: "Keyboard Layout Flags 18.04 (again) how to"
date: 2018-12-23
forum: General Help
---

### Post by Claus7 on 2018-12-23
Hello,

in a brand new installation of ubuntu 18.04 I wanted the keyboard layout to be represented using flags and not using letter abbreviation, since, for me, it is much more easier to recognize. I was able to see also, that there are many out there that face the same problem, so I hope that this solution will help.
The thing is that the old good solution was not working in all themes:
[https://ubuntuforums.org/showthread.php?t=2193789&highlight=flag](https://ubuntuforums.org/showthread.php?t=2193789&highlight=flag)

The default flag icons seem to be almost identical for all but a few themes (suru is one) and they are not found under the theme's icons. For example in Adwaita they were nowhere to be found. From the look of the icons though, it seems that they are located under the icon themes ubuntu-mono-light and ubuntu-mono-dark.  

1) For these themes the old solution is still working:
you create a 22x22 svg icon flag (just converting a png one will work for example:
convert indicator-keyboard-En.png -resize 22x22 indicator-keyboard-En.svg
would suffice)
and then you will have to place it under /usr/share/icons/ubuntu-mono-light/status/22

2) For the other themes even if you place them under the same location the flags won't appear.

3) Also the solution to enable flags from dconf did not work either (even if taking into consideration to place both png and svg files under .icons or even .icons/flags)

4) what I did is that both in the theme of choice and for the aforementioned themes I added the flags as mentioned previously. Then, I went to the suru icon theme and transfered the lang folder (which contains the scalable folder) in the corresponding location of my icon theme of choice. For some reason the flags were recognized even if under the lang folder there were no flag icons.

I hope that it helps,
Regards!

---

