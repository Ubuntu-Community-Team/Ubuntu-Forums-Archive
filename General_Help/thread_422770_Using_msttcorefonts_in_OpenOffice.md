---
title: "Using msttcorefonts in OpenOffice"
date: 2007-04-25
forum: General Help
---

### Post by mjpatey on 2007-04-25
Hello,

I've installed msttcorefonts, and they do appear in my font listing when I try to change system fonts.

However, I'm following OpenOffice's guide for "adding" fonts to OpenOffice, so they can be used by it... and have no idea where the MS fonts are located.

I've tried looking in the "Font Folder" (///fonts), I've tried "slocate" to find individual fonts, but the msttcorefonts don't show up anywhere by their usual names, at least.  In addition, when I tried looking for the standard fonts using slocate (like "sans," for example), they showed up in many places, none of which seemed like an actual font folder.

Anybody know where the msttcorefonts go when installed, so I can let OpenOffice know about them?

Thanks!

-Mark

---

### Post by trotur on 2007-04-25
> **mjpatey said:**
> Anybody know where the msttcorefonts go when installed, so I can let OpenOffice know about them?

You should look for directory /usr/share/fonts/truetype/msttcorefonts

---

### Post by mjpatey on 2007-04-25
That's where they are!  Thank you!

Unfortunately, OpenOffice still isn't showing them in the Fonts list, even though I added them.  Any idea how to fix this?  I know it's a long shot.

---

### Post by Hagar Delest on 2007-04-25
Try to put the folder with the fonts in your user profile ~/.fonts. I've noticed that OOo has better eyes when it looks in this user folder.

---

### Post by trotur on 2007-04-26
If you want the fonts to be added for all users, do following in terminal
```
sudo ln -s /usr/share/fonts/truetype/msttcorefonts /usr/lib/openoffice/share/fonts/msttcorefonts
```

---

### Post by mjpatey on 2007-04-26
Merci, Hagar... but I didn't get your suggestion until after trying trotur's suggestion, which worked!

Thank you, trotur, it worked like a charm!

-Mark

---

### Post by trotur on 2007-04-26
> **mjpatey said:**
> Thank you, trotur, it worked like a charm!

I'm so glad to hear that! :)

PS. There is a useful OOo wiki in [http://wiki.services.openoffice.org/wiki/Font-FAQ](http://wiki.services.openoffice.org/wiki/Font-FAQ)

---

