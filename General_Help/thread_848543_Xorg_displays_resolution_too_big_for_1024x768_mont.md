---
title: "Xorg displays resolution too big for 1024x768 montor, help?"
date: 2008-07-03
forum: General Help
---

### Post by Dwedit on 2008-07-03
Xorg is displaying a resolution too large for the 1024x768 monitor.  How do I stop this?
In the logon screen, it displays in the invalid resolution.
In Gnome, it obeys my setting for 1024x768.
In KDE, it displays the invalid resolution.

I have the blank xorg.conf file that Ubuntu comes with, which has nothing anywhere to set resolution options.

How do I force xorg to never display anything beyond 1024x768?

---

### Post by trevelyan on 2008-07-03
type this in a terminal:
sudo gedit /etc/X11/xorg.conf

but i dont remember exactly what it is you have to change.. i think it was something related to the "screen" section. and change the resolution to something else (even if its already what you want it to be). then log out and then back in.. and then change it to what you actually want it to be and then log out and see if its fixed now.

maybe someone else can be a lil more accurate... but if not.. you can still give it a try.

---

