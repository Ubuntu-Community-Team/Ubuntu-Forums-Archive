---
title: "A Bunch of Dumb Questions"
date: 2004-11-20
forum: General Help
---

### Post by rikkulinux on 2004-11-20
[FONT=Book Antiqua]
I just installed xmms to listen to mp3s.  How do I open it?  There isn't an icon in the Applications menu.  Is this any better than Totem?

Do icons get created in the Applications menu automatically when the programs are installed?  If not, how do I put them there.

How can I change it so that the window tabs in the bottom panel stay in the order I open them, and don't get sorted by type or whatever the are trying to do there.  (If I need a new desktop I'll open one, thanks gnome, quit sorting my window for me).

Finally, a rant:  I can't believe anyone thinks Natalus's default action of opening a new window for ever folder is better than a file manager...  That was the first thing I fixed after Ubuntu was installed.

-rikku

[/FONT]

---

### Post by hitchhiker on 2004-11-20
How did you fix Nautilus, the window opening is a right royal pain.

When I installed XMMS, it gave me an icon in the Mutimedia menu.
Same with gxine, except I got an entry but no icon next to it.
I've tried adding an icon but everytime I reboot it's dissappeared again.

HH.

---

### Post by rikkulinux on 2004-11-20
[QUOTE=hitchhiker]How did you fix Nautilus, the window opening is a right royal pain.
[/QUOTE]
[FONT=Book Antiqua]
Go to Computer > Desktop Preferences > File Management

Click on the 'Behavior' tab and check the 'Always open in _b_rowser windows' box.

Still working on those Applications menu icons,
rikku
[/FONT]

---

### Post by ynef on 2004-11-20
Adding items to the applications menu is either handled by the package you install, or by hand. I think that the official Ubuntu packages are supposed to add themselves to the menu, but if you install debian packages then you're (often) out of luck.

To add to an already existing folder in the Applications menu, you go to it and right click and select "Entire menu" -> "Add new item to this menu". A window appears and you fill out the fields to match whatever program you just installed.

To add a new folder to the Applications menu itself, open Nautilus and in the address bar go to:
```
applications:///
```

You can now add a new folder like usual.

To fix the grouping feature, yes -- it's annoying, you right click on that little dotted vertical bar next to the "Show desktop" button in the lower left corner of your screen and choose properties. You'll get a window that has the option you want to modify.

Edit: Oh, as for xmms, you start it with the command xmms :) In case you hadn't figured that one out on your own. You can run it from a terminal.

---

### Post by Rancoras on 2004-11-20
[QUOTE=rikkulinux]I just installed xmms to listen to mp3s.  How do I open it?  There isn't an icon in the Applications menu.  Is this any better than Totem?[/QUOTE]

If you log out and back in, the launcher will appear in the applications menu. (assuming you installed via synaptic or apt-get)  FWIW I think it's better than Totem, but that's all personal preference.

---

### Post by rikkulinux on 2004-11-20
[FONT=Book Antiqua]I ran xmms from the terminal and somehow that made the icon show up in the Applications menu.  Thanks for the help.

I'm still not really clear on the grouping thing and resorting in the panel.  Do have have to change the maximum and minimum size of the bars also?  I checked "Never Group Windows", but it is still re-sorting them for me...

Thanks,
rikku
[/FONT]

---

### Post by adbak on 2004-11-20
For playing MP3s in XMMS, make sure that you apt-get install libmikmod2.  That's needed for MP3 support.

---

