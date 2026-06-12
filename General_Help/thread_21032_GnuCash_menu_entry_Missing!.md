---
title: "GnuCash menu entry Missing!"
date: 2005-03-20
forum: General Help
---

### Post by rykel on 2005-03-20
Hi,

I installed GnuCash via Synaptic from GNOME environment (universe), and it runs fine...

However, I have to start it from commandline and there is NO menu entry for it in GNOME or KDE... yes, sure, I created a launcher for it in the panel, BUT I cannot find its official icon...

I reinstalled it thru' Synaptic and still, no menu entry either way... 

Or do I simply do a Complete Removal via Synaptic, and try again?

Can you please advise me on what I can do to setup my GnuCash menu entry properly?


Best Regards,

Rykel
Singapore

---

### Post by kperkins on 2005-03-20
The icon should be in /usr/share/pixmaps/gnucash/
Gnucsh is in my Applications menu under Debian > Apps > Tools (don't ask me why, that's where it ended up when I upgraded)

---

### Post by Mike Buksas on 2005-07-15
Did you refresh the panel with:

```
killall gnome-panel
```

Restarting GNOME should do the trick as well.

---

### Post by geofff on 2005-08-04
I know this is an old thread but I've just had the same problem after installing via the Unofficial Starter Guide. For anyone else searching, my answer was to ensure I had no spaces after each line of entries in /usr/share/applications/GnuCash.desktop per [http://ubuntuguide.org/index.html#gnucash](http://ubuntuguide.org/index.html#gnucash) Hope this might help someone.

---

