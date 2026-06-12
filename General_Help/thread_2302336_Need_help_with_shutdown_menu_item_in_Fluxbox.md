---
title: "Need help with shutdown menu item in Fluxbox"
date: 2015-11-09
forum: General Help
---

### Post by can5 on 2015-11-09
Hello, I installed Ubuntu Minimal (without any tasksel items) and I'm using Fluxbox as a window manager.

The problem is my pc hangs after I click the menu item I created, it can't shutdown completely.

I added user to sudoers file and here's the code I found:

```
[exec] (Shutdown) {xterm -e sudo shutdown -h now}
```

I tried exiting Fluxbox first however my code didn't work at all. How can I fix this problem?

---

### Post by raketax on 2015-11-12
Replace the -h with -P

---

### Post by can5 on 2015-11-12
wow it's working! you are great.

---

