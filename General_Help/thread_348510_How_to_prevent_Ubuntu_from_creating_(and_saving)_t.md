---
title: "How to prevent Ubuntu from creating (and saving) thumbnails?"
date: 2007-01-28
forum: General Help
---

### Post by emarkay on 2007-01-28
Never needed them in Windows, and don't need them now.  They just take up space and are a security risk.

How to disable creation of them everywhere, all-the-time?

---

### Post by yigal.weinstein on 2007-01-28
By this do you mean the pictures you see in Nautilus of your documents?

---

### Post by yabbadabbadont on 2007-01-28
Depends on which desktop environment you are using.  In Gnome, you need to change the settings in Nautilus.  Edit->Preferences->Preview tab->set them all to never.  Then remove the ~/.thumb* directory.  Unfortunately, some other programs may create thumbnails on their own and may or may not have preferences you can change.  You'll just have to look and see in each case.

---

### Post by noynac on 2007-01-28
--Deleted__

---

### Post by emarkay on 2007-01-29
> **yabbadabbadont said:**
> Depends on which desktop environment you are using.  In Gnome, you need to change the settings in Nautilus.  Edit->Preferences->Preview tab->set them all to never.  Then remove the ~/.thumb* directory.  

That says "Show Thumbnails".  SOMEWHERE I remember something that gave an option to "create thumbnails" with a checkbox - some obscure GNOME setting I stumbled upon, but I just can't find it now....

---

### Post by allwin on 2007-01-29
Try running gconf-editor?  Maybe there is a setting inside there someplace, just pulling it out of my hat.

---

### Post by emarkay on 2007-01-29
Maybe in Applications/System Tools/Configuration Editor - //apps/nautilus/preferences/thumbnail_limit ?

What if I made that "0" (zero)?

Aha!  Here it is! 
//apps/desktop/gnome/thumbnailers/disable_all

"Set to true to disable all external thumbnailer programs, independent on whether they are independently disabled/enabled"

Yippee!  :)

---

### Post by Pobega on 2007-01-29
*What* is creating thumbnails though? What program? gnome-screenshot?

---

### Post by emarkay on 2007-01-29
Video, image, applications...  ther are 44 listed of which 9 create thumbnails by default:
PDF, X-DVI, X-FONT, X-GNOME, .vnd/djvu(Evince), and apparently the image editor programs add them to the filenames by default.

---

### Post by yabbadabbadont on 2007-01-29
> **emarkay said:**
> Aha!  Here it is! 
//apps/desktop/gnome/thumbnailers/disable_all

"Set to true to disable all external thumbnailer programs, independent on whether they are independently disabled/enabled"

Yippee!  :)

I second that emotion!  Yippee!  :D

Thanks for finding that.

---

