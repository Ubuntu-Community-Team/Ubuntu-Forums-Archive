---
title: "I lost login.keyring"
date: 2008-06-28
forum: General Help
---

### Post by 3mpy on 2008-06-28
Hi, I deleted all files in .gnome2/keyrings because I read somewhere it would all regenerate and I wouldn't need to put my password everytime I logged in to use the wireless, but nothing regenarated, and when I start ubuntu it says authentication failed and I can't do anything, not even log in. So I can't use my computer at all, except through recovery mode, with the root shell. Can anybody help me?

Cheers from Paraguay,

Mauricio

---

### Post by Vadi on 2008-06-28
Try doing

sudo apt-get remove libpam-gnome-keyring

and then

sudo apt-get install libpam-gnome-keyring ubuntu-desktop

---

