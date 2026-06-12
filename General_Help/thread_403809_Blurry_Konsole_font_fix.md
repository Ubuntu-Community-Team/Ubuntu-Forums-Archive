---
title: "Blurry Konsole font fix"
date: 2007-04-07
forum: General Help
---

### Post by twstokes on 2007-04-07
I'm not sure how many other people have had this issue but it drove me up the wall after doing a clean install of Kubuntu Edgy on two machines. I found that after I changed any display settings my Konsole fonts (and possibly others) would get really blurry.

To fix it I removed ".fonts.conf" from my home directory, and removed the line "XftHintStyle=hintmedium" from ~/,kde/share/config/kdeglobals. 

Now everything is nice and clear again. After doing this if I go back and try to change display settings again, ".fonts.conf" will be generated but won't cause any trouble for me. I did have some issues with the MS Fonts but I just removed them and if I need them later I'll find a way to make it all work.

Possibly this has already been solved by someone on the forum, but just in case it hasn't I wanted to share. :) 

I've also attached a picture of what the fonts look like normal and blurry. Also, here's a bug report I found that someone made: [https://launchpad.net/ubuntu/+source/kde-systemsettings/+bug/69085/+viewstatus]("https://launchpad.net/ubuntu/+source/kde-systemsettings/+bug/69085/+viewstatus")

---

