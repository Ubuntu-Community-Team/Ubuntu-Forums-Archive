---
title: "bug in gnome panel"
date: 2007-09-06
forum: General Help
---

### Post by InGunsWeTrust on 2007-09-06
When I log in there is a blank box and in the panel there is an application "gnome-panel" If i close it nothing else goes in the panel for the rest of the time I am logged in. Obviously the panel itself is appearing in the panel which probably shouldn't happen.

---

### Post by mocoloco on 2007-09-07
Wow, that's a cool one :).  Try closing it, then right-click the panel and add the Window List (that's what shows the running windows in the panel).  That will probably work, but I'm suspicious it would happen again after logout/login.
If so, you could see if it happens under other user's accounts.  If not, the file for your panel is in ~/.gconf/apps/panel/general and it's called %gconf.xml.  You could make a backup of it, then try replacing it with one from another user, or removing it completely and see if Gnome re-creates it.
Hopefully one of those things will work.

---

### Post by InGunsWeTrust on 2007-09-07
It is actually a really wierd bug. It happens sporatically. Sometimes I log in and nothing is wrong and sometimes I'll log in 2-3 times in a row and it will always be there. Like I said if i close it has the same effect if you killed the process gnome-panel. If you open any other ap that should appear in the panel it doesn't. I fear editing the .gconf.xml file though because I don't think there is any configuration that would do something like "show the panel in my panel cuz i'd really like to see it" Also if there was there would be no way of knowing if it worked because it happens sporatically

---

### Post by JungleJoker on 2007-09-11
Not that this is of any help, but I have the same problem. Now and then an empty gnome-panel appears at login...

---

### Post by InGunsWeTrust on 2007-09-11
Post a screen shot of yours too. Also do you use beryl also? It may be a bug in beryl not gnome.

---

### Post by FuturePilot on 2007-09-11
I've had that happen to me sometimes. A few times it didn't say Gnome panel but Mixer Applet. :o And I'm running Compiz Fusion.

---

### Post by InGunsWeTrust on 2007-09-13
Sometimes I get Trash applet too! I think this is more of a beryl/compiz error than a gnome bug! If you reload window manager from the beryl manager it disappears without closing it!

---

