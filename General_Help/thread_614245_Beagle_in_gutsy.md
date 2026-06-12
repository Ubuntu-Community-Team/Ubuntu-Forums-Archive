---
title: "Beagle in gutsy"
date: 2007-11-15
forum: General Help
---

### Post by Virgofenix on 2007-11-15
I've installed an old version of Deskbar (the one with the entry panel layout) and Beagle search, as the old deskbar doesn't have a plugin for Tracker in Gutsy. 

My problem: Beagle doesn't start up and operate in the background like it did in Feisty. My deskbar has 0 results from beagle, although, if I run beagle itself, I do get results; so it isn't because it hasn't finished indexing.

---

### Post by dbera on 2007-11-16
> **Virgofenix said:**
> 
My problem: Beagle doesn't start up and operate in the background like it did in Feisty. My deskbar has 0 results from beagle, although, if I run beagle itself, I do get results; so it isn't because it hasn't finished indexing.

What do you mean "Beagle doesn't start up and operate in the background" ? What are you doing and what happens ? Since it is an old deskbar, it is possible that it the old deskbar wont work with the newer libbeagle (the API that deskbar uses to talk to beagle).

---

### Post by Virgofenix on 2007-11-16
Yeah, I checked the Processes on System Monitor and saw a beagle entry. However, there isn't an icon present (the magnifying glass icon) on the notification area.

Actually, the reason I installed Beagle, when I already have Tracker, is because I anticipated that the API you're talking about wouldn't be compatible with deskbar. I have Tracker and the Beagle in the repositories installed; and have enabled the Files/Folders and Beagle searches in the preferences of my deskbar.

---

### Post by dbera on 2007-11-17
> **Virgofenix said:**
> Yeah, I checked the Processes on System Monitor and saw a beagle entry. However, there isn't an icon present (the magnifying glass icon) on the notification area.

If you saw "beagled" in the processes, then its the search daemon. The icon is present if you start beagle-search GUI (with --icon) - there should be an entry for the GUI somewhere in the menu; i dont remember offhand what it is.

---

### Post by Virgofenix on 2007-11-18
> **dbera said:**
> If you saw "beagled" in the processes, then its the search daemon. The icon is present if you start beagle-search GUI (with --icon) - there should be an entry for the GUI somewhere in the menu; i dont remember offhand what it is.

By "menu" do you mean the preferences menu of Beagle?

Beagle also doesn't launch by pressing F12 (and I enabled that feature). My primary concern is why the results from beagle aren't showing up in deskbar. Btw, the link in this post is the .deb of the deskbar I'm using: 
[http://ubuntuforums.org/showpost.php?p=3181461&postcount=177](http://ubuntuforums.org/showpost.php?p=3181461&postcount=177)

---

### Post by Virgofenix on 2007-11-20
Bump. Please help.

---

### Post by dbera on 2007-11-20
> **Virgofenix said:**
> By "menu" do you mean the preferences menu of Beagle?
Nops ... gnome menu. Or you can start it from command line as "beagle-search --icon".

Beagle also doesn't launch by pressing F12 (and I enabled that feature). 

- This probably broke in Gutsy. Its already fixed upstream and will be available in the next release.

My primary concern is why the results from beagle aren't showing up in deskbar. Btw, the link in this post is the .deb of the deskbar I'm using: 
[http://ubuntuforums.org/showpost.php?p=3181461&postcount=177](http://ubuntuforums.org/showpost.php?p=3181461&postcount=177)

- Thats fine, but I wont be surprised if the old deskbar does not work with latest beagle. Try to start beagle-search as "beagle-search --icon", see if the GUI comes up and returns search results.

---

### Post by Virgofenix on 2007-11-21
I'm such an idiot.

I checked sessions and saw that the beagle search tool (not the daemon) was unchecked. The F12 summon works now. I'll see if I can get results now via deskbar.

---

### Post by Virgofenix on 2007-11-23
Still no results from beagle via deskbar.

I went back to synaptic and reinstalled libtracker and the other deskbar related stuff when I uninstalled the deskbar that came with Ubuntu. No luck, as of yet.

---

### Post by [ajax] on 2007-11-27
Beagle runs on my Gusty install.  There was no need to downgrade your version of Deskbar.  If you revert to the new one (doesn't that ring bells of "back to the future"?) and reinstall both it and beagle it might work out.

---

### Post by Virgofenix on 2007-11-27
I didn't like the UI in the new deskbar. I'm trying to make Beagle work with the old one.

---

