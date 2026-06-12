---
title: "Trouble with menulibre and alacarte"
date: 2014-05-22
forum: General Help
---

### Post by Edward_Diener on 2014-05-22
I had installed the latest version of menulibre as a replacement for the oft-buggy alacarte. After using menulibre to add a menu entry to the Ubuntu 14 menu system, and dragged my menu item to the launcher, now whenever I try to open either menulibre or alacarte I get the same crash from either. The crash says:

```
menulibre crashed with SIGABRT in g_assertion_message.
```

OR

```
alacarte crashed with SIGABRT in g_assertion_message.
```

Executing menulibre from the terminal gives:

```
ERROR:/build/buildd/gnome-menus-3.10.1/./libmenu/gmenu-tree.c:4022:preprocess_layout_info: assertion failed: (!directory->preprocessed)
Aborted (core dumped)

```
Executing alacarte from the terminal gives:

```
(alacarte:5035): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(alacarte:5035): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
**
ERROR:/build/buildd/gnome-menus-3.10.1/./libmenu/gmenu-tree.c:4022:preprocess_layout_info: assertion failed: (!directory->preprocessed)
Aborted (core dumped)
```

It looks like menulibre may have fouled up some menu system file when I used it as a replacement for alacarte. I know that I did not dfirectly access any meny system file.

Any help solving this problem would be appreciated. I do have Ubuntu backed up so I can try replacing a menu system file with a backed up version to fix the problem if I new which file was broken if that is causing the problem.

---

### Post by bluesabre on 2014-05-23
This is a known issue with MenuLibre 2.0.3.  We have a fix available in Ubuntu 14.10, which will be making its way to 14.04 shortly.


In the meantime, you can install version 2.0.4 from the MenuLibre Stable PPA in Ubuntu 14.04.  This will require that you replace your menu file (~/.config/menus) with an older copy.  Then this issue will be resolved.  To install the PPA:


sudo add-apt-repository ppa:menulibre-dev/devel
sudo apt-get update
sudo apt-get install menulibre

---

### Post by Edward_Diener on 2014-05-25
> **bluesabre said:**
> This is a known issue with MenuLibre 2.0.3.  We have a fix available in Ubuntu 14.10, which will be making its way to 14.04 shortly.


In the meantime, you can install version 2.0.4 from the MenuLibre Stable PPA in Ubuntu 14.04.  This will require that you replace your menu file (~/.config/menus) with an older copy.  Then this issue will be resolved.  To install the PPA:


sudo add-apt-repository ppa:menulibre-dev/devel
sudo apt-get update
sudo apt-get install menulibre

I installed the backup of the ~/.config/menus directory and its files, but I am still seeing the same problem just executing alacarte. Is it possible something else has to be changed rather than just the files in the ~/.config/menus directory ?

The files are restored from the backup were before I tried to install menulibre in Ubuntu 14 AFAICS.

---

