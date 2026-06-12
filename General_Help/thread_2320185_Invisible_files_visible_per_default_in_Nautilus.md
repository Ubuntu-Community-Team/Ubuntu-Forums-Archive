---
title: "Invisible files visible per default in Nautilus"
date: 2016-04-11
forum: General Help
---

### Post by schnuckenack2 on 2016-04-11
Hello,

somehow in Nautilus all files are visible per default. When I use the menu to make them invisible they will stay so for that instance. As soon as I open another instance, it shows all the invisible files again. 

Where can I find the appropriate config file to make files and directories beginning with a dot invisible per default?

Thanks!

---

### Post by grahammechanical on 2016-04-11
You are right. I am using 16.04 with Files version 3.14.3. We can change this behaviour by going to Edit>Preferences>Views & removing the check mark against the box labelled "Show hidden & backup files." 

Regards.

---

### Post by deadflowr on 2016-04-11
It seems to be a problem with dconf settings.
I notice that if I untick show hidden in nautilus' menu and then tick reset to defaults, it reverts back to showing hidden.(?)

But when I open dconf-editor and go to org > gtk > settings > filechooser and highlight *show-hidden*, if i uncheck it (or select the set to default option in the bottom right corner)
It resets the defaults to not show hidden.

So it seems like the dconf settings are overriding the nautilus settings.

---

### Post by schnuckenack2 on 2016-04-13
Thank you both for your answers. **deadflowr** 's solution worked for me. +1 up

cheers

---

### Post by schnuckenack2 on 2016-04-13
Sadly I must correct myself. Nautilus is still showing the hidden files no matter what its Preferences are.

---

### Post by mc4man on 2016-04-13
> **deadflowr said:**
> It seems to be a problem with dconf settings.
I notice that if I untick show hidden in nautilus' menu and then tick reset to defaults, it reverts back to showing hidden.(?)

But when I open dconf-editor and go to org > gtk > settings > filechooser and highlight *show-hidden*, if i uncheck it (or select the set to default option in the bottom right corner)
It resets the defaults to not show hidden.

So it seems like the dconf settings are overriding the nautilus settings.
If you are referring to View > Show Hidden .. or View > Reset View to Defaults than that's - 
Just a view, not a preference setting
Once any setting is changed in Edit >  Preferences > * or dconf  then that change becomes the defacto default as far as  in app menus (other than Edit > Preferences.

---

