---
title: "OpenOffice doesn't see my fonts"
date: 2006-12-24
forum: General Help
---

### Post by justinjacobs on 2006-12-24
Hi everyone. This one has had me stumped for a while. I have a bunch of Truetype fonts installed  on my Edgy system. I installed them by dragging them to the **fonts:///** folder in Nautilus, followed by running:
```
fc-cache -fv
```
This was seemingly successful, as the fonts show up in the Font Preferences dialog, Gaim, GIMP, and all of my other GTK applications. However, when I use OpenOffice, I can't selected any of my fonts for use. Any ideas of why this is? :confused: 

Also, I'd like to note that I was able to use this same procedure on my other Edgy system, and it worked perfectly. ](*,)

---

### Post by Hagar Delest on 2006-12-28
If you put your fonts files in the user profile (/.fonts), it should work fine.

---

### Post by justinjacobs on 2006-12-29
Thanks for the suggestion, but unfortunately, it didn't work. I even tried running fc-cache again. I tried using KControl to add the fonts. However, they didn't show up in the Font Installer list. :(

---

### Post by Hagar Delest on 2006-12-29
That's weird, usually, there is no problem with that. See here perhaps : [Getting Fonts into OO]("http://http://www.oooforum.org/forum/viewtopic.phtml?t=39820").

---

