---
title: "How to rid the screen of the icon menu bar on left side"
date: 2014-09-15
forum: General Help
---

### Post by oldefoxx on 2014-09-15
I was wiorking quite happily with 13.10, but a VirtualBox upgrade to 4.3.16 hobbled my PC so that nothing worked right.  I decided to go ahead and upgrade to Ubuntu 14.04 so as to see if that would help get my machine untangled.  I've done that, but now I need to get rid of the icon bar on the left side so that the full virtualbox client screen will display.  Can someone tell me how to do that and revert to the old method of having the original choices of Applications Places and System display along the top?

---

### Post by deadflowr on 2014-09-15
Install gnome-panel
```
sudo apt-get install gnome-panel
```
then logout and in the login box where your username and password are put, look in the corner for and icon(ubuntui logo) at click it then see the options. You should now see options for ubuntu gnome flashback and gnome flashback -compiz( or effects) select either of the flashback options and you'll get the old applications places menu stuff, and the icon launcher shpould be gone, or at least is suppose to be gone.

I would have to ask, as an aside, what desktop did you have running on 13.10? 13.10 and 14.04 have almost the exact same desktop by default.

---

