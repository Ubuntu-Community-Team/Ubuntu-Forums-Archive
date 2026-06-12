---
title: "disappearing windows"
date: 2007-10-21
forum: General Help
---

### Post by Hex42 on 2007-10-21
i have ubuntu 7.10. i just upgraded from 7. i had beryl installed on 7 for a while but something got f***ed up and i got rid of it. now i can't see utorrent (installed through wine.) it runs, downloads and uploads, i just can't see the actual window for it and thus i can't add torrents and such. the icon shows up in the system tray so that's how i know its dling or uling. i tried the "hide/show window" right click option but nothing happens.  i also installed azureus and im having the same problem. i start it up and get the initial screen but after it says "initializing main window" a screen pops up for half a second, then it disappears. 

also if i minimize something, i can only unminimize it by maximizing it to take the whole screen. once i do that i can't change it back to the original size. its really starting to get annoying. 

anyone got any ideas?

---

### Post by al2cane on 2007-10-26
Unbelieveable! 

Have been searching around since this morning. Having exactly the same problems with uTorrent and Azureus. Azureus pops up for about a second though, and then the window minimises itself (that's what it animates as doing), but there's no tray icon, and no taskbar icon.

Very frustrating considering BitTorrent and BitTornado's download speeds are pathetic by comparison.


*edit*

Workaround to get uTorrent back from reading <s>this post</s> crap, had so many tabs open on it, I can't find it in my history.


Close uTorrent from the tray icon. Open a terminal, and from your home folder [~]:

```

cd .wine/drive_c/windows/profiles/USERNAME/Application\ Data/uTorrent
rm settings.dat*

```

That should remove settings.dat, and settings.dat.old
Reopen uTorrent, go to Options > Preferences and untick "Minimise to Tray". 

Obviously this isn't a solution, but it might take the edge off your nerves until a proper fix is released :-)

---

### Post by ginnie6 on 2007-10-26
why not just use Ktorrent? I've had good results with it.

---

### Post by al2cane on 2007-10-26
It's always better to address a problem with a solution, rather than ignoring it ;-)

---

