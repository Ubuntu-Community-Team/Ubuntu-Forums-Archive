---
title: "xserver over a network..."
date: 2008-03-20
forum: General Help
---

### Post by What The Deuce on 2008-03-20
Okay, i saw this done and I, for the life of me, cannot reproduce it.

"Some guy" running Ubuntu used his macbook's monitor as an extended monitor for his linux box.  They were on the same network and I figure he just did some fancy work with the xserver or something.

The closest i can get is ssh with x11 forwarding...but I am pretty sure he configured his macbook display to be used over a network...anyone have any idea how to do that?

Thanks,
-Deucy...

---

### Post by nsche on 2008-03-28
On the macbook he set up authorization (using Xauth or one of the other options) to allow connections from the linux box.  On the macbook using some terminal program he could then enter a command like [FONT="Comic Sans MS"][SIZE="3"]rsh linuxbox 'xterm -display macbook:0.0'[/SIZE][/FONT]

Alternatively on the linux box he could set up something like xdm or gdm to accept connections and then start up a X server on the macbook with a command something like [FONT="Courier New"][SIZE="3"]Xserver -query linuxbox :1[/SIZE][/FONT] which would open another server on the macbook and give you a login screen to log in to the linux box.

---

