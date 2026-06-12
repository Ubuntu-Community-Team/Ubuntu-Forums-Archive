---
title: "Configuring a newly installed mouse??"
date: 2006-11-22
forum: General Help
---

### Post by johann_p on 2006-11-22
I just replaced my old USB optical mouse by a new USB optical mouse with much higher resolution. 

This works, to some extent, but the mouse pointer moves much too fast on the screen.

Here is what I tried and what did not work:
* In Gnome I selected preferences->mouse from the menu and tried to change the sensitivity. However, moving the slider does not change anything at all. Changing the speedup does change things, but is not what I want.

* In KDE the mouse configuration does not even include a way to change sensitivity, only acceleration. 

No matter how I use these two config options, the mouse is much too fust in the login manager window.

Finally I tried to change this by editing xorg.conf. I added Option         "Resolution"  "<value>" to the mouse device section, varying value from 800 to 3600 (true resolution is 1600) but NOTHING AT ALL changed.

(Yes I restarted the X server with ctrl-alt-backspace after each change in xorg.conf).

Any ideas?

---

