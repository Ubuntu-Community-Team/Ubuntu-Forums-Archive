---
title: "Resolution problem after running Starcraft"
date: 2007-02-03
forum: General Help
---

### Post by Xenophoribic on 2007-02-03
I installed and ran Starcraft, had to close out. Afterwards, my resolution was put at 800x600@50Hz. Okay, no problem, just change it. Wrong. My only options are 800x600 and 50Hz. I also can't change them in nVidia X server.

---

### Post by Polygon on 2007-02-03
hmm, sorry for the stupid question, but did you restart your comp to see if the option magically came back?

---

### Post by Xenophoribic on 2007-02-03
Yes, I did, many times now, no change.

---

### Post by kodoku on 2007-02-04
You need to reconfigure X

Open up a terminal and type:

sudo dpkg-reconfigure -phigh xserver-xorg

Follow the onscreen instructions (use Tab key and space bar to select options) and you should go to a screen that asks for resolutions and refresh rates.

Reboot afterwards

---

### Post by Xenophoribic on 2007-02-04
I've tried that many times now

---

