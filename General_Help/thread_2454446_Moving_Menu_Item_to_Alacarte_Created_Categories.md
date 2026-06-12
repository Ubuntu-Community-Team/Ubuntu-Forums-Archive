---
title: "Moving Menu Item to Alacarte Created Categories?"
date: 2020-11-30
forum: General Help
---

### Post by rebeltaz on 2020-11-30
Y'all helped me a long time ago in moving menu items from one category to another by editing the text files in /usr/share/applications but I have a new query. I have a category that I created using the Alacarte Main Menu Editor called 'cnc'. I edited one of the programs on the /applications directory and changed the 'Category=' to 'cnc' (without the ' obviously) but that doesn't work. How can I get that program to show up in the chosen menu category?

---

### Post by Frogs Hair on 2020-11-30
Please specify desktop environment and Ubuntu version.

---

### Post by rebeltaz on 2020-11-30
I'm sorry. It's Ubuntu 18.04 with gnome flashback

---

### Post by GhX6GZMB on 2020-11-30
I'm not sure that you can create Categories just as you like.

Normally, you need to stick to the registered categories (and sub-categories) as defined here:

[https://specifications.freedesktop.org/menu-spec/latest/apa.html](https://specifications.freedesktop.org/menu-spec/latest/apa.html)

What can be done is to modify the menu headlines in:

/etc/xdg/menus/lxqt-applications.menu

while staying with the registered categories. Not recommended, though, an update might overwrite this file.

Mind you, I'm on Lubuntu (LXQt), so this might not apply 100% to Gnome.

Concerning the directories you mention:
/usr/share/applcations is for the admin user.
$HOME/.local/share/applications is for the normal users, so that each user can have her/his own menu.

---

### Post by rebeltaz on 2020-12-02
> **ml9104 said:**
> I'm not sure that you can create Categories just as you like.

:) You can with the Alacarte Main Menu Editor. 

> **ml9104 said:**
> Concerning the directories you mention:
/usr/share/applcations is for the admin user.
$HOME/.local/share/applications is for the normal users, so that each user can have her/his own menu.

That is good to know. Thank you.

---

