---
title: "quick beryl configure help"
date: 2007-01-20
forum: General Help
---

### Post by cptjaben on 2007-01-20
I'm trying to install and configure beryl following [this guide.]("http://doc.gwos.org/index.php/BerylOnEdgy") Everything seemed to install fine, but when I load up Beryl-manager, I get this message in the terminal and then beryl-manager reverts my window manager back to metacity.

```
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```

Anyone know how to fix this? Thanks much.

---

### Post by cptjaben on 2007-01-21
I got it to work, by following [this guide]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")

---

