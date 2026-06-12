---
title: "Classic GNOME gone?"
date: 2014-12-03
forum: General Help
---

### Post by Tom_Hoff on 2014-12-03
Hi All

I had it set up so that I was using GNOME with the classic menus and bars. Pretty sure it was "GNOME Flashback (Compiz)" in the sessions menu.

I had the wobbly windows effects too, so I definitely had compiz running. Then I just HAD to mess with .profile files in compizconfig-settings-manager. Ever since, I can't get my original DM back, every time I select Flashback compiz, I get unity. 

[https://drive.google.com/file/d/0Bxm6iIIPXQ77UzBDZDZqUV9xZ2s/view?usp=sharing](https://drive.google.com/file/d/0Bxm6iIIPXQ77UzBDZDZqUV9xZ2s/view?usp=sharing)

Any ideas how to fix this? I've tried default settings in compizconfig, no luck

Tom

---

### Post by CantankRus on 2014-12-03
You probably **are** in the **gnome-fallback-compiz ** session but somehow the unity plugin has been enabled in compiz.
Check your session....
```
echo $DESKTOP_SESSION
```

If your in the right session, disable the unity plugin using ccsm.
You may need to enable the window decorations plugin as well.

I find the compiz settings seem to get mixed up when swapping between the unity and gnome-fallback-compiz sessions.

---

### Post by Tom_Hoff on 2014-12-04
You're a lifesaver, thank you! :)

---

### Post by Yougo on 2014-12-04
compiz does support setting up profiles, so that you can load a profile, depending on your session. 
you could make a new profile and mess around in that one while keeping the 'Unity' profile working :-)

[http://wiki.compiz.org/CCSM#Profiles](http://wiki.compiz.org/CCSM#Profiles)

i can't seem to find how to link a custom profile to a session though.

Unity session uses the 'Unity' profile
all other sessions use the 'default' profile

---

