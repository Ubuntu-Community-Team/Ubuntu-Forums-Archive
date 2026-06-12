---
title: "gufw not working"
date: 2014-04-21
forum: General Help
---

### Post by nLpPyXR on 2014-04-21
I'm running Lubuntu core 14.04 over the Trusty Tahr Ubuntu mini.iso, and for some reason gufw won't launch after I enter my password.

After entering "gufw" manually in the terminal and entering my pw in the window that pops up, I get the following output in Xterm:

```
Traceback (most recent call last):
  File "/usr/share/gufw/gufw/gufw.py", line 21, in <module>
    from view.gufw  import Gufw
  File "/usr/share/gufw/gufw/view/gufw.py", line 19, in <module>
    from gi.repository import Gtk, Gdk, WebKit
ImportError: No module named gi.repository
```

---

### Post by shadytv on 2014-04-21
It looks to be an issue with python, does uninstalling/reinstalling it help?

---

### Post by nLpPyXR on 2014-04-21
if you mean reinstalling gufw then no, it doesn't help...

---

### Post by nLpPyXR on 2014-04-21
pardon the double-post but I've also tried installing a package called "python-ufw" through synaptic and that didn't work either...

I'm a member of a private tracker so not being able to seed torrents due to closed ports is very troublesome for me.

---

### Post by shadytv on 2014-04-21
> **nLpPyXR said:**
> if you mean reinstalling gufw then no, it doesn't help...

No I mean reinstalling python. The error you're getting looks to be related to python.

---

### Post by nLpPyXR on 2014-04-22
Google truly is a great friend.

Turns out I was missing a package called python-gobject; installed it and gufw works flawlessly.

Thread marked as solved.

---

