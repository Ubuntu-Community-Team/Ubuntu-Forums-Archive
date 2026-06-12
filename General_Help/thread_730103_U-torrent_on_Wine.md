---
title: "U-torrent on Wine"
date: 2008-03-20
forum: General Help
---

### Post by Moonfrost on 2008-03-20
So I've been using Utorrent with Wine for 2 months and it used to work flawlessly...until a few days ago when I start it, it starts minimized to try and when I click "hide/show utorrent" utorrent doesn't show up at all! I tried uninstalling it from Wine and deleting any file I found with the name utorrent and after re-installing I still get the same issue!

I also tried uninstalling Wine and re-installing it and still the same thing...does anybody know what it could be? and no, I'm not willing to use another bittorrent client because that's the only department where Linux lacks since most of them are pretty slow compared to utorrent...

---

### Post by alejandro.mc on 2008-03-21
OK so this is what I do when that happens. It didn't happen a lot with the previous version of Utorrent, and it has not happened to me with the current version of Utorrent. Nevertheless if it's happening to you this is what you should do. Close Utorrent. Then open your home folder, press Ctr + H to have access to hidden files, enter .wine folder, enter drive_c folder, enter windows folder, enter profiles folder, enter the folder with your home name, enter application date folder, enter utorrent folder, AND know delete the settings.dat and settings.dat.old files. Once you erased those two files, open Utorrent, you'll have to set it up again, but the program will be there and you'll be able to manage your downloads, just don't minimize again to the tray (in fact simply disable the tray option).

Good luck.

---

### Post by Moonfrost on 2008-03-22
> **alejandro.mc said:**
> OK so this is what I do when that happens. It didn't happen a lot with the previous version of Utorrent, and it has not happened to me with the current version of Utorrent. Nevertheless if it's happening to you this is what you should do. Close Utorrent. Then open your home folder, press Ctr + H to have access to hidden files, enter .wine folder, enter drive_c folder, enter windows folder, enter profiles folder, enter the folder with your home name, enter application date folder, enter utorrent folder, AND know delete the settings.dat and settings.dat.old files. Once you erased those two files, open Utorrent, you'll have to set it up again, but the program will be there and you'll be able to manage your downloads, just don't minimize again to the tray (in fact simply disable the tray option).

Good luck.

Thanks a lot! that worked...and I never really checked that Utorrent had an option to disable the tray icon...again, thanks!

---

