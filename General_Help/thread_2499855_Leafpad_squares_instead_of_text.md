---
title: "Leafpad squares instead of text"
date: 2024-08-13
forum: General Help
---

### Post by msknight on 2024-08-13
Ubuntu Cinnamon 24.04

I did a fresh install, but ended up in trouble with snaps and apparmor. I needed to put some software into complain mode (so that they could access files on a mounted SMB share) but because Firefox was getting in the way, someone on this forum prompted me to the solution which was to remove the firefox snap and install it another way.

However... during the process of messing around with all this, my favoured editor Leafpad (which is a snap) doesn't display text any more, it displays squares instead.

Grateful for any thoughts how to resolve this mess I've got myself into please.

---

### Post by guiverc on 2024-08-13
Have you tried going into *Options* and then *Font* and ensuring the font you have selected is still available??

Squares can appear (*instead of characters*) if the selected font in the configuration file doesn't actually exist (ie. no characters to display; so a box-like character is used instead).

I'm not using your release (*nor your desktop*), but I didn't experience or couldn't experience any issues there...   If that doesn't solve your issue, or you wish to explore what settings you have, maybe looking in

```

~/snap/leafpad/current/.config/leafpad/leafpadrc

```

is where I'd look next.

---

### Post by msknight on 2024-08-13
Thanks. Didn't work, unfortunately. Reporting Monospace and looking much like the leafpad configuration on another system. Removing and reinstalling the snap also doesn't work. Deleting those configuration files and letting it re-create them also didn't work.

---

### Post by msknight on 2024-08-13
I followed this and it looks like it's sorted.
[https://askubuntu.com/questions/1224125/font-characters-displayed-as-squares-in-ubuntu-18-04](https://askubuntu.com/questions/1224125/font-characters-displayed-as-squares-in-ubuntu-18-04)

Many thanks for your time.

---

