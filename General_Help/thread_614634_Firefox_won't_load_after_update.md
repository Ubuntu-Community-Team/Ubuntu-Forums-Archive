---
title: "Firefox won't load after update"
date: 2007-11-16
forum: General Help
---

### Post by wsscott on 2007-11-16
I run the software updates whenever notified.  A recent update killed Firefox and it will not load.  I believe it was an upgrade to compiz.  I uninstalled and reinstalled Firefox but Firefox still will not load.

---

### Post by hotstyle765 on 2007-11-16
try typing firefox in a terminal. What does it say?

---

### Post by wsscott on 2007-11-16
command not found

---

### Post by hotstyle765 on 2007-11-16
Looks like firefox might not be installed.

Run in the terminal

```
sudo apt-get install firefox
```

and try running firefox again from the terminal

---

### Post by wsscott on 2007-11-17
Ran "sudo apt-get install firefox" in terninal.  No change.  Firefox seems to load, but is not visable. If I attempt to open firefox after my initial attempt, I get a message that "Firefox is already running but is not responding. To open a new window you must first close the existing firefox process, or restart your system."

---

### Post by wsscott on 2007-11-17
Completely removed firefox and then reinstalled.  It still will not load. Moving to Opera

---

