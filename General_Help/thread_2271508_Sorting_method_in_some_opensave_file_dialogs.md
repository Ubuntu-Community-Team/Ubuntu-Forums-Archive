---
title: "Sorting method in some open/save file dialogs"
date: 2015-03-30
forum: General Help
---

### Post by Dennis N on 2015-03-30
Xubuntu and Lubuntu 14.10 and 15.04 beta:

Some open/save file dialog windows are sorting files and directories intermingled instead of the standard sorting of directories before files. I saw this in Xubuntu and Lubuntu 14.10 and now 15.04 betas. Only some applications do this: Mousepad, Abiword, Gnumeric and Audacious are four of them I have noticed in Xubuntu.

Questions: Can these be changed through some option/setting to the standard way of listing directories before files? The way they work now is visually confusing and takes more time to drill down through several levels of subdirectories. And what package would handle this sorting?

Attached is test using Mousepad's open file dialog. Note intermingled directories and files.

---

### Post by ajgreeny on 2015-03-30
Same here running Xubuntu 15.04 as a VM in VBox.

Very annoying!

---

### Post by Toz on 2015-03-30
> **Dennis N said:**
> Only some applications do this: Mousepad, Abiword, Gnumeric and Audacious are four of them 
All these apps are GTK3 apps. To change GTK3 apps so that the folders appear first:
```
gsettings set org.gtk.Settings.FileChooser sort-directories-first true
```

---

### Post by Dennis N on 2015-03-30
> All these apps are GTK3 apps. To change GTK3 apps so that the folders appear first:
gsettings set org.gtk.Settings.FileChooser sort-directories-first true

Thanks. Just the setting I was looking for. Problem Solved.

---

