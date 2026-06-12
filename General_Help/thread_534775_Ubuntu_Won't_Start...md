---
title: "Ubuntu Won't Start.. :|"
date: 2007-08-25
forum: General Help
---

### Post by guswashere on 2007-08-25
Well I'm back with another problem... When i try and turn on the computer... it says that it failed to start the X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

then it displays info about my computer... 


What should I do? :confused::confused::confused:

---

### Post by pizzutz on 2007-08-25
what info does it display?

---

### Post by merlinus on 2007-08-25
You might try this:

Press "Esc" when prompted to display the grub boot menu, boot into recovery mode, login...then enter:

(or Ctrl-Alt-F1 to get to prompt)

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

