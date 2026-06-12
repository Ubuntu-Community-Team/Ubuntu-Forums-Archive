---
title: "pb with keyboard"
date: 2005-10-17
forum: General Help
---

### Post by gdcondor on 2005-10-17
hi

i just updated from hoary : on my other computers, all went fine (or easy to correct)
but with this one after updating i've the following pb :

- no usplash instead of usplash it seems to text boot written very very very small (totally unreadable) : hopefully gnome started !
- in gnome i've some refresh rate pb with my screen :( it was working fine under hoary but apparently breezy detects it incorrectly (it's a packard bell vt700 flat panel) : i tried to change it in xorg;conf (sorry i can't make "point" see my next pb) looking on the internet for the correct refresh rate but it's still not working
- i've the same pb as many of you with the keyboard but i'm using only one keyboard scheme (fr) and not switching between many of them and i don't have some US keyboard instead but something really strange : AZERTY (like on french keyboard) but without a lot of keys (like "point" "slash bar" etc)
i tried this : [http://www.ubuntuforums.org/showthread.php?t=76261](http://www.ubuntuforums.org/showthread.php?t=76261) without any success
i've the same error as in this thread : [http://www.ubuntuforums.org/showthread.php?t=75052&highlight=keyboard+xkb](http://www.ubuntuforums.org/showthread.php?t=75052&highlight=keyboard+xkb) 
("error activating xkb configuration")
i've the following results :
```

$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "fr", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "fr", "", ""
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [fr,us]
 model =
 overrideSettings = false
 options = [grp grp:alts_toggle]
$ setxkbmap fr
Error loading new keyboard description

```
and when i tried to reinstall xkeyboard-config it tells me that /etc/X11/xkb/pc/ was not a real file or link : in fact this file doesn't exist at all
- hal didn't start : i just have a message "failed to initiate hal"
- tomboy crashed on launch : maybe a pb linked with the keyboard
- finally gdesklets is making some strange things but that's not a major issue,,,,

what can i do !! it's really annoying especially the keyboard and screen !! and it was working fine with hoary !

thanks for your help !!
-- 
GdCondor

---

### Post by gdcondor on 2005-10-18
no idea for any of my pb ?? i really need your help :((

---

### Post by gdcondor on 2005-10-18
i solved my pb with the keyboard by putting the whole directory /etc/X11/xkb/ from the livecd .... simple and working.. maybe the updating process forgot this or it was some old files from warty (but it was working under hoary)

for my pb with the screen it could be a hardware pb

but for usplash i have no idea :( for tomboy neither...

---

