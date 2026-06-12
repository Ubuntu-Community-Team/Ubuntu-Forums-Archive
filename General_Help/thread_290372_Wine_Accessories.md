---
title: "Wine Accessories"
date: 2006-11-01
forum: General Help
---

### Post by pt123 on 2006-11-01
I had Wine installed on Dapper, using this as the source.
[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)
But I had to do a clean install of Edgy. I have install Wine from this source. 

On Dapper when I used to run Windows setup up programs Wine would install it and the icon on my desktop with a link to the app.
But now on Edgy it is not doing that. Is there away to turn this feature. Its annoying trying to find a suitable icon etc.

---

### Post by CatKiller on 2006-11-01
You could try running **winecfg** and going to the Desktop Integration tab - there's a box that you can configure to link your pretend Windows desktop with your real Ubuntu desktop. That might help, although I've never tried it.

---

### Post by pt123 on 2006-11-02
^ That doesn't do it. But it is a very nice feature.

---

### Post by CatKiller on 2006-11-03
> **pt123 said:**
> ^ That doesn't do it. But it is a very nice feature.

Oh well. I've not used Wine on Edgy yet. I've not had Windows applications add icons to the desktop on Breezy/Dapper either, though. I guess it depends on the application. I do get launchers in ~/.gnome/apps/Wine, though. If you do too, you could copy these to the desktop.

---

### Post by pt123 on 2006-11-05
Ok found the problem.

 What happened was that I had only installed wine in the official ubuntu depositories and that wouldn't come configured so .exe files are opened up with Wine. So I had to manually add the command "wine" to open exe files. 

But when I added the Wine rep, which I had accidentally left commented, and got the latest version. It automatically adds Open with "Wine Windows Emulator". So now when I open with that it creates the icons on the desktop.

Sorry for the trouble.

---

