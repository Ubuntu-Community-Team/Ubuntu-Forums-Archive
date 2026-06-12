---
title: "Desktop issue, caused by files transferred from old hdd?"
date: 2007-04-27
forum: General Help
---

### Post by Compeau on 2007-04-27
I had a hard drive crash a month ago, but i was able to recover my data and transfer all my important data to my new hdd.  However, I never changed the file permissions, so things were always dicey.  Now I've noticed that on user accounts where there are files from the old drive on the desktop, sometimes when logging in three file explorer windows will be open to the desktop, and the actual desktop will be missing its background image (the ubuntu default one), and will appear empty.  Any idea what's up?

---

### Post by Pox on 2007-04-27
Could be nautilus crashing from a file on the desktop... try going to a terminal and running "sudo chmod -R ugo+rwx ~/Desktop", then restarting the desktop with "nautilus &".

That's assuming you're on standard ubuntu and not kubuntu or xubuntu, though.  Xubuntu is "xfdesktop &" instead of nautilus, don't know about kubuntu.

---

