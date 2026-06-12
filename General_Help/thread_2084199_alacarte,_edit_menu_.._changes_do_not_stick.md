---
title: "alacarte, edit menu .. changes do not stick"
date: 2012-11-14
forum: General Help
---

### Post by linuxcss on 2012-11-14
after fresh install of xubuntu 12.10
invoking alacarte and then using edit menu ... changes do not stick

also just ran updates today, still broken

anybody have a fix for this?

---

### Post by Leo H on 2012-11-16
The 'Main Menu' editor (alacarte) is in fact completely broken in xubuntu 12.10.  Changes in the xubuntu Applications Menu made with alacarte are not effected.  For example:

-- Ticking/unticking boxes in alacarte does not stick (as reported above).
-- New menu items created with alacarte are not put in place.
-- Menu items deleted with alacarte remain in place.
-- Moving items from one menu folder to another with alacarte no longer works.
-- .desktop files of any menu item opened (with or without (!) change) in alacarte simply accumulate in /home/[user]/.local/share/applications, without further effect.
-- sudo alacarte in a terminal no longer works.

It appears that alacarte is dependent on an item (gnome-desktop-item-edit) provided by the gnome-panel package which is not not compiled with alacarte and which is not otherwise installed under xubuntu.  (See also Launchpad Bug #656735 -- [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/656735](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/656735)).

However, the full gnome-panel package is an alien package under xfce, and it should not be installed under xubuntu as it pulls in a mass of redundant and undesirable non-xfce gnome desktop functionality.  (Note:  exo-utils for xfce, which provides exo-desktop-item-edit, _is_ fully installed but this does not resolve the above bugs.)

Apart from these bugs, alacarte has limited functionality, it is prone to crashing, and it is awkward to handle.  Many of these problems have a very long history and are never properly addressed.

It seems better if the alacarte Applications Menu Editor in xubuntu would be replaced as standard (or at least as an option through the (x)ubuntu repos) by LXMenuEditor.  This menu editor is currently maintained at  [http://lxmed.sourceforge.net/](http://lxmed.sourceforge.net/).

I have filed a Launchpad bug report at [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/1079953](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/1079953)



SYSTEM USED: Fresh install of xubuntu 12.10 (i386) using the official xubuntu .iso image, fully updated as of today.

---

### Post by pqwoerituytrueiwoq on 2012-11-16
i just edit the .desktop files in /usr/share/applications with nano

Hidden=true will hide it in the menu

---

### Post by rai4shu2 on 2012-11-17
Alacarte still works fine for me (using 12.04). Anyone try out this alternative?

[https://launchpad.net/~menulibre-dev/+archive/devel](https://launchpad.net/~menulibre-dev/+archive/devel)

---

### Post by Frogs Hair on 2012-11-17
Alacarte  works fine for me on XFCE 4.10 session in 12.10. I'm either lucky or not  affected Xubuntu bug.

---

### Post by vasa1 on 2012-11-17
[http://ubuntuforums.org/showpost.php?p=12357937&postcount=4](http://ubuntuforums.org/showpost.php?p=12357937&postcount=4)

---

