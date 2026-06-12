---
title: "Yucky Openoffice icons won't change."
date: 2008-05-11
forum: General Help
---

### Post by macaholic on 2008-05-11
I recently installed the openoffice 3 beta, read about my crappy experience [here]("http://ubuntuforums.org/showthread.php?t=789622"), and now the disgusting looking icons refuse to change. When I try to change them in tools > options > view, absolutely nothing happens. Is there some text config file I can change somewhere manually?

---

### Post by mano cazalet on 2008-05-11
well, finally you managed to compile it, congratulations :)

i'm not sure maybe the were left out? 
i've just checked my icons are stored in 
/opt/openoffice.org/basis3.0/share/config

images_industrial.zip  images_tango.zip  and so on

maybe if u just copy an ooo image package there from your 2.4?

ps.:sry if that sounds dumb, it's just I know nothing about compiling

---

### Post by macaholic on 2008-05-11
Unfortunately I didn't actually compile it, and i got really close too :(, I had to force install the deb package. Those files are all there, and I can select them in the options, but they don't change.

---

### Post by macaholic on 2008-05-12
Anyone have any ideas? This has relly been bugging me, the icons it's choosign are terrible.

---

### Post by macaholic on 2008-05-12
Now I'm totally confsued, I have nuked any icons that would possibly be left on my system that have anything to do with openoffice, and they are STILL THERE. I tried changing file names to switch it for the icons I wanted, but no good. Please can someone help me?

---

### Post by calc on 2008-08-05
Depending on what it looks like this might be a known issue in OpenOffice.org, they put the program into High Contrast mode when the theme is dark, which means the icons look a bit weird compared to the rest of the desktop.

[http://www.openoffice.org/issues/show_bug.cgi?id=80636](http://www.openoffice.org/issues/show_bug.cgi?id=80636)

---

### Post by Locutus_of_Borg on 2008-08-06
regenerate your icon cache

no idea of the command to do that on ubanto

fc-cache probably

---

