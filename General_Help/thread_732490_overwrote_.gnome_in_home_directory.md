---
title: "overwrote .gnome in /home directory"
date: 2008-03-23
forum: General Help
---

### Post by danbuter on 2008-03-23
I accidentally overwrote the .gnome file in my home directory. Will this really screw up my system, or was it just a text message saying you are using Gnome v...?

---

### Post by dcstar on 2008-03-23
> **danbuter said:**
> I accidentally overwrote the .gnome file in my home directory. Will this really screw up my system, or was it just a text message saying you are using Gnome v...?

There is no ".gnome" file, there is a ".gnome" directory.

Recreate the directory and restart the X session with CTRL-ALT-BACKSPACE.

---

### Post by danbuter on 2008-03-23
I'm using Hardy Heron. There was a regular file named .gnome, and a directory named .gnome2 which has various files in it. There is no directory named .gnome.

Anyways, I mkdir a .gnome directory, and did the fast reboot. Nothing is in the file after reboot. Maybe Ubuntu is using a non-standard format.

---

