---
title: "distorted screen in some Ubuntu 22.04 help screens"
date: 2023-01-25
forum: General Help
---

### Post by winston61 on 2023-01-25
Hello all- I'm running Ubuntu 22.04 on a Raspberry Pi 4. Everything has been very smooth. However in some apps and in a newsreader, when I press the help key I get a screen with a white background and many broken horizontal lines of different colors. No content displayed. Can anyone offer any insight? Thanks to all.

---

### Post by TheFu on 2023-01-25
What help key?  There's no standard in Linux.  I fear you may be telling the OS to change to a different ptty if it is a function key.  Do r-pis support different ttys?  I don't have a r-pi v4 and don't use my other Pis as desktops so I don't know.

Every program is created by a different team. They choose what the different keys mean.  If the menu doesn't specifically say "F1" next to "Help", then don't assume F1 is a help key.  It isn't.

---

### Post by winston61 on 2023-01-25
When click the question mark(?) at the left side of the  screen(desktop) I get the white screen with broken colored lines

---

### Post by TheFu on 2023-01-25
> **winston61 said:**
> When click the question mark(?) at the left side of the  screen(desktop) I get the white screen with broken colored lines
Sorry, I don't use any DE (desktop environment), so I'm completely unfamiliar with the desktop you are seeing.  
[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/) is the official Ubuntu 22.04 Gnome Desktop Guide.

OT follows:
I wouldn't use a full Gnome desktop on any Raspberry Pi.  I'd probably use Ubuntu-Mate flavor on a Pi v4. It is much lighter than the Gnome3+ version, while still being polished. It has a WinXP feel. If you want something more modern, but that works with fewer resources than Gnome3, check out KDE/Kubuntu.  XUbuntu is probably a little lighter than Mate and Lubuntu would be the lightest of the main DEs.  There are some like Budgie which I hear are lighter, but  I don't know much about them.  Some people really love those.

[https://ubuntu.com/desktop/flavours](https://ubuntu.com/desktop/flavours) has the official flavors list.  The Gnome one gets 5 yrs of support, provided an LTS release is used.  The other official flavors get 3 yrs of support, so 22.04 Kubuntu (and the other flavors) would be supported until April 2025. That's important.  Non-LTS releases have much shorter support periods. just 6-9 months.

---

