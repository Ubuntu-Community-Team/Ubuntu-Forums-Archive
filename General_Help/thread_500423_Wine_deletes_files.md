---
title: "Wine deletes files????"
date: 2007-07-13
forum: General Help
---

### Post by djrobthaman on 2007-07-13
Hi there everybody,

Has this ever happened to you?  I downloaded utorrent from their site, put the file in my home folder and typed wine utorrent.exe in my "run application" box. It worked perfectly (the program was a bit ugly, almost as if I had loaded ubuntu without gnome-settings-daemon, but it worked) and then I turned it off.  Added a shortcut in the applications menu to run the same command (wine utorrent.exe) but when I tried to launch it through there nothing happened, only to be greeted to the fact that the file was no longer in my home folder.  And now I can't find it.

Does this happen normally???

Can I fix it???

Any ideas????

Thanks

---

### Post by raulteixeira on 2007-09-04
When you run the uTorrent exe file the first time it gets installed into the wine windows drive (Program Files/uTorrent by default). You can find the uTorrent exe file there. By default it will be:

/home/USERNAME/.wine/drive_c/Program Files/uTorrent

To run it, just  "wine" pointing to that and it should work:

wine "/home/USERNAME/.wine/drive_c/Program Files/uTorrent/uTorrent.exe"

---

