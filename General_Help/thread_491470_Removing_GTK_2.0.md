---
title: "Removing GTK 2.0???"
date: 2007-07-03
forum: General Help
---

### Post by Combat on 2007-07-03
I downloaded the source for GTK 2.10 and compiled/installed it. Now my Add/Remove programs isn't working, and file-roller doesn't work anymore either.

When i try to run Add/Remove programs, it  opens and a window opens with a progress bar on it that says "Checking installed and Available applications..." The progress bar finishes, but the window never closes. Since the window never closes, i can't use Add/Remove programs. I tried typing "xkill" in the terminal and then clicking on the window, but it doesn't work! My pointer turns into the scull and crossbones, but it doesn't do anything when i click the window.

As for file-roller, it opens and everything, i can browse files inside an archive, but i can't extract. When i try to extract a window opens so i can choose where to extract, but when i hit ok, it just crashes.

I'd like to remove the version of GTK i installed. How do i do that?

---

### Post by Brucevdk on 2007-07-03
Move into the source directory and use:
```

sudo make uninstall

```

Then (but I'm not sure about this) you'll probably want to reinstall libgtk2.0.
```

sudo apt-get --reinstall install libgtk2.0-0

```

---

