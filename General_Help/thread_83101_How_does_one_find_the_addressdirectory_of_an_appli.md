---
title: "How does one find the address/directory of an application?"
date: 2005-10-27
forum: General Help
---

### Post by autonomy on 2005-10-27
I'm trying to browse for an application to have it start up with GNOME. How do I find it? Where do applications normally go when installed?

---

### Post by stuporglue on 2005-10-27
A lot of stuff will be in /usr/bin. 

If you know the name of the command, you can type:

$ which programname

and it'll tell you where it's at.

---

### Post by Remmelas on 2005-10-27
which, as mentioned is great, so is 'whereis' and 'locate'

---

### Post by autonomy on 2005-10-28
thanks, y'all, but neither command worked; and i couldn't find Firestarter in the usr/bin. I read that it's supposed to start in the background, but I just like to see it minimized to the tray. someone, help please.

---

### Post by bionnaki on 2005-10-28
typing

> whereis firestarter

did nothing?

---

### Post by autonomy on 2005-10-28
eh, i capitalized it! lower case showed me. thanks

---

### Post by 23meg on 2005-10-28
Open Synaptic, find the package that your program is in, right click it, choose Properties, and hit the "Installed Files" tab.

---

### Post by az on 2005-10-28
[QUOTE=autonomy]thanks, y'all, but neither command worked; and i couldn't find Firestarter in the usr/bin. I read that it's supposed to start in the background, but I just like to see it minimized to the tray. someone, help please.[/QUOTE]
Firestarter has two different sides.  One side is the firewal which runs at boot and sets up your firewall rules.  The other is the graphical part which you use to define those rules.  If youinstall firestarter and tell it to go, every time you boot, the rules will be in effect.

You can add firestarter to your session startup, so that you get the graphical part, too, every time you start up.

---

### Post by autonomy on 2005-10-28
thanks, is there a way to make sure it's running?

---

