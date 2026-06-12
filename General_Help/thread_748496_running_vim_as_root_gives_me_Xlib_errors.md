---
title: "running vim as root gives me Xlib errors"
date: 2008-04-07
forum: General Help
---

### Post by Mlehliw on 2008-04-07
The title basically says it all. I almost always use vim to edit text and so when I'm editing system files I run vim as root. I'm not sure when this error cropped up but I just noticed it today, but whenever I run vim X gives me the following error. It can be quite annoying if vim inserts this text in the file I'm trying to edit.

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

---

### Post by Mlehliw on 2008-04-08
If anyone else has this problem and finds this post. I had to uninstall gvim. I don't know why though, I manual linked /usr/bin/vim to /usr/bin/vim.basic instead of /usr/bin/vim.gtk. It appears that vim.basic would still try to open an X connection?

---

