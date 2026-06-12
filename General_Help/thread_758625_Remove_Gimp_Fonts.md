---
title: "Remove Gimp Fonts"
date: 2008-04-18
forum: General Help
---

### Post by hulio40 on 2008-04-18
i would like to remove the basic fonts from the gimp so i can find the fonts added by me easily how do i do that i dont find any font files in the gimp dir except those added by me

---

### Post by hulio40 on 2008-04-18
anyone? :confused:

---

### Post by hulio40 on 2008-04-19
:(:(:(:(     pls help someone cmon

---

### Post by fragos on 2008-04-19
Gnome has a font cache that links to fonts from many directories. Applications like Gimp go to this common font cahe. Remove fonts and they will also be lost to other applications like OpenOffice.

---

### Post by hulio40 on 2008-04-20
> **fragos said:**
> Gnome has a font cache that links to fonts from many directories. Applications like Gimp go to this common font cahe. Remove fonts and they will also be lost to other applications like OpenOffice.

and were can i find that cache? i really dont need those fonts they all look the same

---

### Post by Can+~ on 2008-04-20
Well, gnome adds a quick access via "fonts:///", but if you need the full path:

```
/usr/share/fonts
```

I would suggest you, to leave it as it is. I never quite understood the system on which fonts are added, the thing I understand, is that you append font folders with fc-cache, you should look more information before trying to delete anything.

---

### Post by fragos on 2008-04-21
Run synaptic and search for "ttf". You will find a number of font sets you'll want to delete. Uninstall them and they will be removed from the cache for you. That is the simplest way. Some fonts are called out in the ubuntu-desktop package. In this case it will ask to unistall that as well. Since it's only a list of packages you can uninstall it without loosing another of the referenced packages. You will however create a problem if you wish to upgrade to a future release. 

You can also just delete the font files from disk and run "sudo fc-cache -fv" to rebuild the cache.

---

### Post by hulio40 on 2008-04-21
would it be possible to rename the .ttf file font name to a then an other one to   b so they stay at the top.  this would do the work for me, i dont want to mess up my system,    renameing its title.ttf doesnt do anything. or do i need a speial font editor

---

