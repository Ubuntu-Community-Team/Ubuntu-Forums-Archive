---
title: "OpenOffice weird problem"
date: 2008-06-05
forum: General Help
---

### Post by FerBatista on 2008-06-05
I have a folder with some .doc .xls .odt .ods files, some of each type open flawlessly other don't (it doens't matter if were created by OO or not). In the ones that don't it still show the openoffice splash screen but nothing else happens. But If I open openoffice first and from there choose the document it opens all of them, the problem only happens when opening from nautilus.

Why does this happen? Any ideias?

One more thing, on some of the documents that fails (not all), if I put them on other folder they will open.

---

### Post by FerBatista on 2008-06-05
BTW, I'm using x64 8.04.

---

### Post by FerBatista on 2008-06-05
UPDATE:
Opening one of the files that doesn't open, it shows a file called ".lock" in "/home/fernando/.openoffice2", that file never disappears. With the files that work as they should the file disappears when I close the openoffice file.

It's a text file that says the following, if it helps:

> [Lockdata]

User=fernando

Host=fernando-desktop

Stamp=B78806D6A80AC87C6DD5657BC53F92C3

Time=Thu Jun  5 16:57:22 2008

IPCServer=true



After trying some solutions and desinstalling and reinstalling OO, I got to the conclusion that the problem is related to the packages "openoffice.org-gnome" and/or openoffice.org-GTK", desinstalling these two packages make the program work fine. Of course now openoffice doens't use any of my theme settings.

So I'd still love to ear an opinion how to work this out.> 

---

### Post by FerBatista on 2008-06-06
Anyone? Please

---

### Post by forestpixie on 2008-06-06
Make sure that you have no oo files open and delete the .lock file and try again, I'd reinstall the packages you uninstalled.

---

### Post by FerBatista on 2008-06-06
> **forestpixie said:**
> Make sure that you have no oo files open and delete the .lock file and try again, I'd reinstall the packages you uninstalled.

Thanks by the tip.

But I already tried that, in fact I deleted all the folder, but it still didn't work. So far the only thing that worked is uninstalling those packages.

---

