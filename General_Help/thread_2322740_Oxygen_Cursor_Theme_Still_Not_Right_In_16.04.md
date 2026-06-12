---
title: "Oxygen Cursor Theme Still Not Right In 16.04"
date: 2016-04-30
forum: General Help
---

### Post by jim_deadlock on 2016-04-30
In 15.10 switching to Oxygen (or other theme) cursors via update-alternatives used to result in Gnome Shell crashing when resizing windows. In 16.04 this has been fixed but the pointers are not showing correctly. I've changed to Oxygen via the Tweak Tool and also update-alternatives, but the window resize cursors are still stuck on DMZ (see screenshots below. This is the only nagging problem I have with 16.04, many other bugs have been fixed and it's lovely. If I can just get this minor issue fixed it will be 100% perfect.

Normal Oxy pointer (correct)
[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/oxy1.gif[/IMG]

Finger (correct)
[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/oxy4.gif[/IMG]

Edge resize (DMZ - wrong)
[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/oxy2_1.gif[/IMG]

Corner rezize (DMZ - wrong)
[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/oxy3.gif[/IMG]

---

### Post by jim_deadlock on 2016-05-01
I have the answer for anyone who's interested. Comparing /usr/share/icons/Adwaita/cursors (default cursors) with /usr/share/icons/oxy-white/cursors I noticed that several files/symbolic links existed in Adwaita which were missing in oxy-white, so I manually added the necessary links in the oxy-white/cursors directory and that did the trick.

---

