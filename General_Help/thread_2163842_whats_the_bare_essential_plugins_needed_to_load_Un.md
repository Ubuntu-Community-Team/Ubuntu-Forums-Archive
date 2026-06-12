---
title: "whats the bare essential plugins needed to load Unity in 12.04"
date: 2013-07-19
forum: General Help
---

### Post by eival on 2013-07-19
im fooling around with CCSM and  already figured out how to get around if it crashes with F3, or just running unity --reset in the terminal

but trying to re-add piece by piece to find the bare essential to make the side and top bars appear is hard.

does anyone know? cause even when i just enabled the Unity plugin by itself, it still didnt load.

ps. outside of installing gnome or xfce,ect.. is there anyway to make windows have the "file edit settings" on the top of their windows, rather than appear in the top of the Unity bar? and even when i maximize, have those stay on each open application as well

---

### Post by grahammechanical on 2013-07-19
So, you disabled the Ubuntu Unity Plugin that you found in CCSM. That is not a good thing to do. In fact in later versions of Ubuntu we just cannot disable the Unity plugin. Have you rebooted? Have you tried re-install Ubuntu-desktop?

To get the look that you want you cannot avoid installing another desktop.

[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

See posts 4.

Regards.

---

### Post by mc4man on 2013-07-20
> **eival said:**
> im fooling around with CCSM and  already figured out how to get around if it crashes with F3, or just running unity --reset in the terminal

but trying to re-add piece by piece to find the bare essential to make the side and top bars appear is hard.

does anyone know? cause even when i just enabled the Unity plugin by itself, it still didnt load.

ps. outside of installing gnome or xfce,ect.. is there anyway to make windows have the "file edit settings" on the top of their windows, rather than appear in the top of the Unity bar? and even when i maximize, have those stay on each open application as well

The min would be 
unityshell, OpenGl, Composite, Gnome compat, expo, compiz library toolbox, scale

That doesn't mean it would be very usable, this are pretty much needed - 
place windows , resize window ,  move window,  window decoration

Good to enable for various reasons - 
Workarounds, regex matching

If you want more than 1 workspace then either wall or cube/rotate, viewport switching 

As far as disabling unity in ccsm - actually not a bad idea to do when making some changes, can reduce compiz crashing while in ccsm, just remember to re-enable. (unity can be disabled in any version of ubuntu inc. 13.10

Sometimes in 12.04 you'll need to just force a log out if compiz gets too stuffed from ccsm changes, no big deal
(enabling ctrl+alt+backspace to kill xserver is useful in such cases, - system settings > Keyboard >  Layout Settings > Options > Key Sequence  to kill the  Xserver

---

