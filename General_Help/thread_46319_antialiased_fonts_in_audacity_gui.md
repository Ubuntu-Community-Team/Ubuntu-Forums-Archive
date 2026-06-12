---
title: "antialiased fonts in audacity gui?"
date: 2005-07-04
forum: General Help
---

### Post by renick on 2005-07-04
Because I'm new to Linux, I still haven't adjusted to some GUI issues in various applications. Can someone explain to me how I can get the fonts in the interface to Audacity (and a variety of other programs) to be antialiased?

I've got Gnome and KDE installed with antialiasing turned on in both of them. Audacity, however, is still painful to look at. What can I do?

---

### Post by jarrett.wold on 2005-07-06
I took a peek around, it looks like Audacity 1.2 is built on GTK+1.x.  There's a solution out there for enabling anti-aliasing for GTK+1.x applications.  Fair warning I haven't tried it:

[http://gdkxft.sourceforge.net/](http://gdkxft.sourceforge.net/)

However, if you want to check out and build Audacity 1.3 source (unstable) from CVS, they're enabling GTK+2.x by default.

I'd be interested to hear if you got gdkxft working.

---

### Post by renick on 2005-07-10
Thanks! Since this says a botched install can break X, I'm going to wait until later this week (after I finish some critical school assignments) before I attempt it. I'll post here on how it goes.

---

