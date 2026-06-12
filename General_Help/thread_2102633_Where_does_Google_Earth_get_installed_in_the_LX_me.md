---
title: "Where does Google Earth get installed in the LX menu?"
date: 2013-01-07
forum: General Help
---

### Post by Rocket J Squirrel on 2013-01-07
I used Synaptic Package Manager's entry for Google Earth ("googleearth-package") but when it finished I can't find Google Earth in any of Lubuntu's LX menus.

---

### Post by Fredo_p on 2013-01-07
It's under the "Internet" drop down.

---

### Post by Rocket J Squirrel on 2013-01-07
But it's not.

---

### Post by vasa1 on 2013-01-07
Just to be clear: was the installation successful and can you get GE to work by any means whatsoever?

If the installation was okay and the program runs but you just don't see it in Lubuntu's menus, it is *possible* that you may need to edit a .desktop file as I suggested here:
[Cannot find firefox in Lubuntu desktop]("http://askubuntu.com/a/231936/25656"). Of course, you'll need to modify things based on the program concerned. But, in short, the villain maybe a line with something like "OnlyShowIn=Unity" which may need to be deleted or commented out since you're on Lubuntu.

---

### Post by Rocket J Squirrel on 2013-01-08
Thank you. 

Yes, I did leave out an important bit of information. After you asked I searched the drive for it (find / -name earth | more) and it turned up nothing. It looks like GE didn't get installed, and there is a very simple reason for that: I didn't read the description of "googleearch-package" in Synaptic Package Manager -- it's a "utility to automatically build a Debian package of Google Earth"

I found the package at [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html) and it installed just fine. Sorry about the premature post.

---

