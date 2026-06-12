---
title: "Font Rendering - Blurry/thin fonts"
date: 2024-03-02
forum: General Help
---

### Post by csete on 2024-03-02
I've recently installed Ubuntu 23.10 on a Dell XPS 15 9520 (2022 version) with a 1920x1200 display resolution.  I can't put my finger on it, but it just doesn't seem like the font rendering looks very good on this machine.  If I boot into Windows, fonts seem clearer, so I don't think it is the display itself, but something about font rendering.  I've tried messing around with Gnome Tweaks font settings to see if I could find something that looked better, but despite seeing changes, none of the options seems significantly better to me.  Am I missing something?  

[ATTACH=CONFIG]293455[/ATTACH]

Thanks,
Craig

---

### Post by #&amp;thj^% on 2024-03-02
I had to check, because I run such new/devel sources, but check if this is installed:
```
 rmadison fonts-ubuntu-classic
 fonts-ubuntu-classic | 0.83-6ubuntu2 | mantic/universe | source, all
 fonts-ubuntu-classic | 0.83-6ubuntu2 | noble/universe  | source, all

```
the package I refer to is:
```
sudo apt installfonts-ubuntu-classic
```
Also from your screenshot>>>Font hinting to "Slight"

EDIT: If that works for tell apt to hold it, to prevent newer fonts being updated:
```
sudo apt-mark hold fonts-ubuntu fonts-ubuntu-console
```

---

### Post by csete on 2024-03-03
Whew.  Much better.  I'm guessing my previous machine still had the old fonts installed despite being updated to 23.10.  This seems much better.  
Thanks!

---

### Post by #&amp;thj^% on 2024-03-03
I remember that from testing 23.10 the fonts just did not look good until i added the Classic fonts back.
Glad to hear your sorted out.

---

