---
title: "Shortcut keys for gftp"
date: 2008-01-25
forum: General Help
---

### Post by Dwood108 on 2008-01-25
Does anyone know what are the keyboard shortcuts for gftp?

I would like to be able to open a file for editing without having to scroll through the menu, similar to how you can just use ctrl+o to open a file in fireftp.

Thanks

---

### Post by gvartser on 2008-01-25
* right click .> edit

/G

---

### Post by Dwood108 on 2008-01-25
I discovered that I can edit the gftpprc file in the .gftp directory so that double clicking a file opens it in the default editor.

Find this line and set the value to 1

# This defines what will happen when you double click a file in the file
# listboxes. 0=View file 1=Edit file 2=Transfer file
list_dblclk_action=1

---

