---
title: "[SOLVED] Gparted and Gutsy problem"
date: 2008-01-23
forum: General Help
---

### Post by alenis on 2008-01-23
Gparte dused to work fine on my system with Feisty. After upgrading to gutsy, when started from the console it prints:

libparted : 1.7.1
======================
Unable to open /dev/nbd0 - unrecognised disk label.
Unable to open /dev/nbd1 - unrecognised disk label.
Unable to open /dev/nbd10 - unrecognised disk label.
Unable to open /dev/nbd11 - unrecognised disk label.
Unable to open /dev/nbd12 - unrecognised disk label.
Unable to open /dev/nbd13 - unrecognised disk label.
Unable to open /dev/nbd14 - unrecognised disk label.
Unable to open /dev/nbd15 - unrecognised disk label.
Unable to open /dev/nbd2 - unrecognised disk label.
Unable to open /dev/nbd3 - unrecognised disk label.
Unable to open /dev/nbd4 - unrecognised disk label.
Unable to open /dev/nbd5 - unrecognised disk label.
Unable to open /dev/nbd6 - unrecognised disk label.
Unable to open /dev/nbd7 - unrecognised disk label.
Unable to open /dev/nbd8 - unrecognised disk label.
Unable to open /dev/nbd9 - unrecognised disk label.

All these "fake" devices are also listed in the gui. Plus, sometimes it crashes just after starting.
Any idea about what could be wrong?

---

### Post by Kingfield on 2008-01-23
It still works though right? You could also use sudo and remove those folders.

---

### Post by alenis on 2008-01-23
Yes it works. I deleted the nbd? files and everything seems to work fine.
Thanks for the advice.

---

