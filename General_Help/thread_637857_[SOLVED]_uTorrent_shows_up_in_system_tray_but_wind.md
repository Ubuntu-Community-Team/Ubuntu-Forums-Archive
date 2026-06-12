---
title: "[SOLVED] uTorrent shows up in system tray but window won't open"
date: 2007-12-11
forum: General Help
---

### Post by inchaos on 2007-12-11
Maybe I'm having a blond moment.
 
uTorrent worked fine the other day, no problems running it with wine whatsoever.

Now for some reason whenever I open/run uTorrent, I can see the icon in the system tray, I can right click it and adjust my download/upload options, but the window for the program doesn't open.  Double clicking it doesn't open the window either, nor does right-clicking and selecting 'hide/show window'.  It's even seeding files, so it's definitely open, but the window refuses to show itself.

I've rebooted, re-downloaded the .exe, nothing.  

I feel really quite stupid at this moment, but I don't know what the deal is.

Are there any linux programs that are known to cause this sort of issue?

---

### Post by matthewcraig on 2007-12-11
Have you tried the default GNOME bittorrent application?

---

### Post by inchaos on 2007-12-11
Yes, it's not my favourite.  


I know there are plenty of other bittorrent clients, but I'm using uTorrent.


It doesn't matter anyway, I figured it out.  Instead of just deleting and re-downloading the .exe, I had to delete all the .inf's and etc...essentially purge the program completely.  I still don't know what caused it but I fixed it for now.

---

