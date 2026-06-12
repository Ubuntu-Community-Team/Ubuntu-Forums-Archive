---
title: "Black dot artifacts appearing ever ~30 seconds"
date: 2014-11-06
forum: General Help
---

### Post by childintime on 2014-11-06
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]On my screen, every 20-100 seconds appears black dots for a split second. I don't know if they appear only in browser or not, but for example they appear in fullscreen Youtube videos as well.[/FONT][/COLOR]
[/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=3]I captured this to show how it looks like:[/SIZE]

[IMG]http://i.stack.imgur.com/ooVyJ.gif[/IMG]

[/FONT][/COLOR]
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]I Don't really want to mess up with my video drivers, because I had long history of problems trying to reinstall them and always getting black screen on reboot. Any ideas how to fix this?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I use Asus K56C laptop with GT 740M nvidia card and Ubuntu 14.04

[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]sudo lshw -c video | grep 'configuration'
**configuration: driver=nouveau  configuration: driver=i915**
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
P.s. I am so disappointed with Ubuntu. I literally have like 5 major issues/bugs which seem to be impossible to fix, and they are extremely annoying. I posted separate topic for each of them but 0 responses :([/FONT][/COLOR][/SIZE]

---

### Post by oldos2er on 2014-11-06
Have you tried the Nvidia proprietary drivers? ```
sudo apt-get update && sudo apt-get install nvidia-current
```

---

### Post by childintime on 2014-11-06
Few months ago I decided to install Nvidia proprietary drivers and I had so much problems with that. Everytime I would boot, I would get black screen, and I tried every single proposed solution and nothing worked, until I somehow fixed it. So this reason I am not going to install those proprietary drivers, unless someone can guarantee it will work 100% (which is not possible I guess).

---

