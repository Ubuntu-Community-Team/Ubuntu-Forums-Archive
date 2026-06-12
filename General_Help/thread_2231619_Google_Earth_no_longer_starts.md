---
title: "Google Earth no longer starts"
date: 2014-06-26
forum: General Help
---

### Post by grey1beard on 2014-06-26
I used Google Earth about a week ago with no problems, but this evening it refuses to start, either from the icon on the taskbar, or from the applications menu.
I ran *sudo apt-get update* and then *upgrade* but still nothing. 
Installed version is 7.1.1.1580-r0 on a 32-bit HP g7000 laptop.
It has occasionally produced odd starting hiccups, but now, other than the brief flash of the black square after clicking on the taskbar icon, nothing else appears.

I have recently installed, not without some problems, DropBox, now working OK. Apart from this, and keeping update manager going whenever it appears, no other changes have been made since Earth ran OK.

Any suggestions ?
Many thanks,
John

---

### Post by monkeybrain20122 on 2014-06-26
Open the file manager to your home directory, press ctrl+h or choose show hidden files in the menu, locate the hidden folder .googleearth (note the '.' in front), open it and delete the file instance-running-lock.
If that doesn't work delete the whole .googleearth folder.

---

### Post by grey1beard on 2014-06-27
Hi monkeybrain20122, and thanks.
I'll keep your instructions on the desktop in case it happens again.
As is the way of these things, it worked 'normally' when I fired it up this morning !
The laptop just showing me whose the boss.
Regards
John

---

