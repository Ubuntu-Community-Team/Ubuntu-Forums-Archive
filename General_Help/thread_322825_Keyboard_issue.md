---
title: "Keyboard issue"
date: 2006-12-21
forum: General Help
---

### Post by oyvindaa on 2006-12-21
Hello good people.

I've got an Acer Aspire 3002LM laptop, and I recently upgraded to Edgy Eft from the update manager.

After installing the driver for my onboard graphics (SiS), some keys on my keyboard stopped working.

It is when I'm going to type these characters it isn't working:

Alt Gr + 2 = @  
Alt Gr + 9 =  ]
Alt Gr + 7 =  \
Alt Gr + 8 =  [

and such.

I've tried reconfiguring xorg but I didn't know what the correct settings are for my keyboard.

Any useful help will be greatly appreciated :)

---

### Post by Unknowndeepness on 2006-12-21
I know you can select keyboard layout in KDE control center, and i've seen acer layouts there. Not to helpful if your on gnome though..

---

### Post by Zalbor on 2006-12-21
I think there's a bug in Edgy that makes AltGr not work... It never has for me, and I remember other threads with people complaining about it.

---

### Post by oyvindaa on 2006-12-21
> **Zalbor said:**
> I think there's a bug in Edgy that makes AltGr not work... It never has for me, and I remember other threads with people complaining about it.

Hm.. that's a bugger.

Is there another way to type those characters though?

---

### Post by tomane on 2007-01-16
Hi, I found that running ```
xmodmap /usr/share/xmodmap/xmodmap.[COLOR=Navy]pt[/COLOR]
``` under kde brought back my ALTGR key on an ASUS F3JC laptop. I don't know how to run it automatically at startup, though.
**NOTE:** the [COLOR=Navy]blue[/COLOR] part of the command should be replaced for the equivalent for the keyboard layout of your country; I use pt for Portugal

Cheers,
--to

---

