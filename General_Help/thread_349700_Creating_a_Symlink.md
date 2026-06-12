---
title: "Creating a Symlink"
date: 2007-01-30
forum: General Help
---

### Post by Graham1 on 2007-01-30
Would someone mind showing me how to create a symlink please? Would prefer in the GUI if possible. If not, the console is fine :). Below is what I'm trying to achieve:-

"in KDE: create a symlink of /opt/connection-manager/systray in this folder: ~/.kde/autostart/"

Am I right in saying that a symlink is similar to a shortcut in Windows?

:)

---

### Post by jpeddicord on 2007-01-30
Yes, symlinks are similar to shortcuts. To create one, here is the terminal command:
```
ln -s /opt/connection-manager/systray ~/.kde/autostart/connection_manager
```

---

### Post by llamakc on 2007-01-30
> **Graham1 said:**
> Would someone mind showing me how to create a symlink please? Would prefer in the GUI if possible. If not, the console is fine :). Below is what I'm trying to achieve:-

"in KDE: create a symlink of /opt/connection-manager/systray in this folder: ~/.kde/autostart/"

Am I right in saying that a symlink is similar to a shortcut in Windows?

:)

ln -s /opt/connection-manager/systray ~/.kde/autostart/systray

No, they're not the same. Here's where to begin in the GUI.

[img]http://i2.sitepoint.com/graphics/creatinglink.png[/img]

---

### Post by Graham1 on 2007-01-30
Sorry, forgot to mention that I'm using Kubuntu (I have Ubuntu too :) ). Tried the links but it's saying "no such file or directory" :confused:.

:)

Edit: Do I need to replace the "~" with "/home/<user>"?

---

### Post by Graham1 on 2007-01-30
Sussed it :D. The autostart folder had a capital "A". Very sneeky :rolleyes:. Thanks for the help guys.

:)

---

