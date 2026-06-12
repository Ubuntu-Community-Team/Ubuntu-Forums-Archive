---
title: "File Manager Issues"
date: 2016-01-13
forum: General Help
---

### Post by adam1234 on 2016-01-13
Hello

I am using Ubuntu Gnome 14.04 LTS, and I am having trouble with File Managers. I primarily want the File Manager to sort "by type", so that folders are listed before files.

I tried changing the relevant DCONF settings for Nautilus (org > gnome > nautilus > preferences > default-sort-settings), but it won't let me change "default-sort-settings" to "by_type". Instead, the setting changed to "modification_date". Now I cannot change that DCONF setting at all; it is apparently stuck on "modification_date", which is EVEN WORSE than "by_name". If I click on "default-sort-settings", there are no other options available. :/

Next, I tried installing Nemo as a File Manager. However, the default colors for the tabs (white text on light-grey background) are pretty much unreadable. I have to put my face directly against my screen in order to read the file tree. :/

Could someone help me solve either one of these issues? I don't care which one. I just want a functional, readable file manager.

Thank you in advance!

---

### Post by deadflowr on 2016-01-13
I think that's the wrong dconf entry.
Go further down to the sort-directories-first option and enable that one.

---

### Post by adam1234 on 2016-01-13
Thanks -- you are correct! That helps me fix one part of the problem. :)

However, the "modification_date" issue persists.

 The setting (dconf > org > gnome > nautilus > preferences > default-sort-settings) is stuck on "modification_date". How can I force it to change back to "by_name"?

Thanks!

---

### Post by deadflowr on 2016-01-13
The default is name, so use the dconf reset command, or in dconf-editor, simply highlight the entry and click set to default in the bottom right corner.

---

