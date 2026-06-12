---
title: "Configuring xDVDShrink"
date: 2007-05-09
forum: General Help
---

### Post by Tombo5150 on 2007-05-09
I am trying to configure this for feisty  and it asks for the name of the dvd device (/dev/dvd). Now I have nodea what they are asking for....any ideas?:confused:

---

### Post by Pox on 2007-05-09
the name of the dvd device should be "/dev/dvd" or "/dev/dvdrw" as far as I know.

---

### Post by StefanoCole on 2007-05-18
If in your computer you have more dvd devices you can tell xDVDShrink which one it has to use (specify it in the form: /dev/hdx, where x is the position of your device (in general b, c or d). If you only have one dvd device or you want to use the default one (as set by Linux) then /dev/dvd should be O.K.

Stefano

---

