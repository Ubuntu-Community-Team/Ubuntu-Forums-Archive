---
title: "new to gnome (from 16.04.3 unity)"
date: 2017-08-07
forum: General Help
---

### Post by Kris_M on 2017-08-07
using classic gnome on my 16.04.3 unity build.(selected via password screen)  The only thing I haven't gotten to work is the "system load indicator" which puts a graph in the top bar - at least it did for unity.This is 3.18 gnome. I remember when I was briefly playing with 3.20 (from the pps's) there was a drawer bottom left > thing that could expand out that had (what used to be in top bar in unity) the indicator for red shift and the psensor icon. That is not here in 3.18 so don't know if that's not a feature or if I have to turn on something in tweak. 4.10.0-30 kern.

edit2: Tried top icons plus extension with no change. I have a bottom bar that shows the open windows that wasn't in 3.20 (shut off windows list extension in tweak but it's still there and functioning)... and no drawer.

edit3: It appears that booting to gnome default instead of classic (password box) and 
adding kstatusnotifieritem/appindicator and deleting topicons does it! 

edit4: that is much too dim to see on the bar (it has a nice graph via - "open system monitor" "resources" so I'll keep it around.)
use gnome extension system-monitor
for ubuntu, do
sudo apt-get install gir1.2-gtop-2.0 gir1.2-networkmanager-1.0  gir1.2-clutter-1.0

---
gparted won't open: solution : in terminal sudo gparted
----
 remember, google is your friend!

No probs at the moment. Marked solved.

---

