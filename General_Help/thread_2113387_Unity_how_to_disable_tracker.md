---
title: "Unity: how to disable tracker?"
date: 2013-02-07
forum: General Help
---

### Post by josm on 2013-02-07
Unity seems to automatically enable and start tracker and index my files.
How can this be prevented or how can I make it so that tracker only runs when and how I want it?
Is it possible to make it so that files are not shown in the dash, only applications?

I already have removed ALL directories from the "Locations" list in tracker-preferences but tracker is still running and seems to still index all my files.

---

### Post by grahammechanical on 2013-02-07
What have you got to hide? Have you run the Privacy utility? There are simple on/off options there.

---

### Post by josm on 2013-02-07
> **grahammechanical said:**
> What have you got to hide?
It should not be of any concern why I want or need  this but here goes: i am on a rather large workstation with millions of files of which practically all are irrelevant whenever I show the dash. It is simply irritating and utterly useless to have totally irrelevant files show up in the dash every time i look for an application there. And I do have my own search utilities for those files on my harddisk which I need to have indexed (documents and source files).

> 
 Have you run the Privacy utility? There are simple on/off options there.
Yes, all switches for "record activity" are set to off there and I still get random files shown in the dash.

This illustrates quite nicely one of the many things that is wrong with Unity: I am the one who wants to tell the system what I need, and I really do not want a system that constantly tries to tell me what I want. Unity does seem to have this is common with GNOME 3: some "UI designers" knowing constantly pretending to know better what I need that I do and taking away control and configuration of all the details away from the user.

---

### Post by josm on 2013-02-08
So IS there a way to prevent tracker from running? 
Although everything is switched off, there are still the processes "tracker-miner-fs" and "tracker-store" store running.

---

### Post by stinkeye on 2013-02-08
> **josm said:**
> So IS there a way to prevent tracker from running? 
Although everything is switched off, there are still the processes "tracker-miner-fs" and "tracker-store" store running.
Yes, don't install it.
Tracker isn't included in the default ubuntu install.

The privacy app controls what is logged by Zeitgeist.
In the privacy app you can turn off online search, delete all your history and
turn off recording by Zeitgeist.
If I do that, Recently Used does not even show up in the dash.

---

