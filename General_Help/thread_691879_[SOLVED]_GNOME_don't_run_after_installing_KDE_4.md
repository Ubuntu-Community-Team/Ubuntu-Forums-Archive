---
title: "[SOLVED] GNOME don't run after installing KDE 4"
date: 2008-02-09
forum: General Help
---

### Post by danielrs on 2008-02-09
I've installed KDE 4 on Ubuntu and now I can't see any login screen (neither gnome nor kde), instead I see a command line.

How can I have gnome running again? and how can I uninstall KDE 4?

---

### Post by danielrs on 2008-02-09
After 3 hours trying to solve the problem, finally solved it.

---

### Post by ultraata on 2008-02-09
Would be fine for you to post solution here.

---

### Post by danielrs on 2008-02-09
I uninstalled gnome using the commands:

```

apt-get remove ubuntu-desktop
apt-get remove gnome
apt-get remove gdm

```

and then reinstalled it again:

```

apt-get install ubuntu-desktop
apt-get install gnome
apt-get install gdm

```

I got all this time to do this because I couldn't discover how to uninstall using command line, I only knew how to install. I discovered it trying every words that could fit there.

---

