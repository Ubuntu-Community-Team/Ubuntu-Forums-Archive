---
title: "Can't  make changes to the Main Menu option in the Settings."
date: 2012-11-14
forum: General Help
---

### Post by Anthony A on 2012-11-14
In the Settings for Xubuntu 12.10 there is a section called "Main Menu". This section is used to set what programs and settings you want to show up in the Main Menu. I can't seem to get any changes I make to stick. When I check a box to select a program or setting the check mark un checks it's self and I can't make any changes. As a result the Main Menu is in default configuration but I would like to make some changes. Why is this happening?

---

### Post by xbunt on 2012-11-16
I have same problem.
Can't change nothing and menu stays default. :???:

---

### Post by badhorse on 2012-11-16
Try deleting:

.config/menus

log out and log in

If not, delete also:

.config/xfce4
.cache/xfce4
.local/share/xfce4

for revert xfce to default settings (log out and log in)

---

### Post by Toz on 2012-11-16
I've noticed this inconsistency as well in 12.10. However, logging out and back in again seems to fix the problem (in that it displays the newly configured menu). Seems to be an issue with the menu re-reading the config file when the application is closed.

If you don't want to log out and back in again, apparently touching the last access time of a desktop file in /usr/share/applications seems to force a re-read as well:
```
sudo touch -a /usr/share/applications/alacarte.desktop
```

As does touching the last access time of a desktop file in your ~/.local/share/applications directory if you have a desktop file there (doesn't require sudo).


_EDIT:_ Might be related to this bug report: [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/1069207]("https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/1069207")

---

### Post by Anthony A on 2012-11-19
Deleting the files did not work.

Logging out and back in did not work either.

When editing the menu the boxes I check mark uncheck them selves right before my eyes. The boxes do not stay checked.

---

### Post by badhorse on 2012-11-20
Read the post form Toz. Is a bug in alacarte. Check the bug report posted above for a workaround.

---

### Post by Anthony A on 2012-11-21
The work around did not work for me.

---

