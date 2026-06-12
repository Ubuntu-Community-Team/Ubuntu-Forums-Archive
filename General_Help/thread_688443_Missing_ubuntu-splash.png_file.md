---
title: "Missing ubuntu-splash.png file"
date: 2008-02-05
forum: General Help
---

### Post by lotuseclat79 on 2008-02-05
I run the Gutsy Gibbon (7.10) Live CD environment, and it appears that there is no ubuntu-splash.png file or link to it in the directory /usr/share/pixmaps/splash or anywhere else.

Can someone please upload the file ubuntu-splash.png as an attachment.

Tia,

-- Tom

---

### Post by danwood76 on 2008-02-05
The ubuntu splash screen is not a .png file.
It is a binary file of some kind.

It can be installed through synaptic/apt, you could always search for usplash to see how to extract/compile the usplash screens.

regards,
Danny

---

### Post by cdenley on 2008-02-05
This package is not installed by default. I'm not sure what it does. It looks like it's just a few images. Since there is a edgy-session-splashes, feisty-session-splashes, but no gutsy-session-splashes, I'm guessing these images are no longer used.
```
sudo apt-get feisty-session-splashes
```
[ATTACH]58798[/ATTACH]

---

