---
title: "AllTunes using Wine"
date: 2007-01-04
forum: General Help
---

### Post by Bealer on 2007-01-04
I've managed to get AllTunes running via Wine.

To do this I've installed Wine, and within the ".wine" directory in my home folder, I've set up all my apps. 

Namely IES4Linux. I've installed this at:
/home/me/.wine/drive_c/Program Files/Internet Explorer

I've then downloaded and installed AllTunes at:
/home/me/.wine/drive_c/Program Files/AllTunes

I grabbed mfc42.dll from my old Windows installation, and placed it (I don't think I needed in both of these but still):
/home/me/.wine/drive_c/Windows/System
/home/me/.wine/drive_c/Windows/System32

I then ran the Wine Configurator, by typing the following in a terminal window:
winecfg

Under "Applications" I created a new app pointing to the alltunes.exe (at /home/me/.wine/drive_c/Program Files/AllTunes). I also set the Windows version to Windows XP.

Under "Libraries" I added "mfc42.dll".



Using the above, I can get AllTunes to run, and IE (used within it) works too. The only problem I've not worked out, is that it won't download any tracks. They just fail. 

Anyone got any ideas?

---

### Post by Bealer on 2007-01-05
Tried a couple more things, but still no luck. 

No one else got any ideas?

---

### Post by zachalekos on 2007-07-29
Still looking for ideas myself

---

