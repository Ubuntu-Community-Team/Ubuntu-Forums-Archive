---
title: "location gedit settings"
date: 2013-06-22
forum: General Help
---

### Post by lou21 on 2013-06-22
Hi,

I have gedit just how I like it on one machine. I want to move this configuation to another. I don't want to move the whole home folder. I have copied. $HOME/.config/gedit $HOME/.local/share/gedit and $HOME/.gconf/apps/gedit-2. What else do I need to move? (My configuration hasn't moved - I've tried loging out and rebooting.)

I am moving from a 12.10 (3.6.1) to a 12.04 (gedit 3.4.1) install (work reasons).

Thanks if anyone can help...

---

### Post by lou21 on 2013-06-25
Bump.  Any ideas?

---

### Post by MidnightGrey on 2013-06-25
apparently mine is located in ~/.gconf/apps/gedit-2/
I am running 12.04

edit: nevermind i checked by changing my gedit preferences and it didnt update.. lol

---

### Post by steeldriver on 2013-06-25
I wonder if you can actually dump them out of the database then import them in?

In 'source' session
```
gsettings list-recursively | grep ^org.gnome.gedit > gsettings.gedit
```

In 'target' session BACK UP YOUR CURRENT SETTINGS
```
gsettings list-recursively | grep ^org.gnome.gedit > gsettings.gedit.bak
```
then import the saved settings from the source session
```
while read -r schema key value; do gsettings set "$schema" "$key" "$value"; done < gsettings.gedit
```

DISCLAIMER: ALTHOUGH I JUST TRIED IT IN A USER ACCOUNT / SESSION I DON'T CARE ABOUT, I HAVE NO IDEA IF IT IS REALLY 'SAFE' - USE AT YOUR OWN RISK! BACK UP YOUR OLD SETTINGS FIRST!!!

---

### Post by mc4man on 2013-06-25
> **steeldriver said:**
> I wonder if you can actually dump them out of the database then import them in?



Seems like a neat little trick, have to keep in mind,  tried here without issue (made on 13.04, reset on 13.10 
Went ahead & also intentionally borked a couple of keys (wrong name), seems it was handled ok (message that key doesn't exist, process stoppped.
Would probably only do this when apps are same version

---

### Post by lou21 on 2013-07-06
Cool.

This is still a bit of a hack and defeats the whole "just move your home folder and all your settings move with it". I think that the likes of gnome and unity are very very broken now. I enjoy tinkering but I don't want to have to mess around customising my text editor every six months...

---

### Post by lou21 on 2013-07-06
Just re-read that and it looks a little bit ungrateful - I'm not thanks I would never have worked that out myself.

---

