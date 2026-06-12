---
title: "Menu entry for GIMP in english?"
date: 2005-10-16
forum: General Help
---

### Post by Mr_J_ on 2005-10-16
I have GIMP, but it's in portuguese, and it's driving me nuts having to translate and find simiral meanings in the things I have to do.

So I can use **[COLOR="Olive"]LC_ALL=en_EN Gimp[/COLOR]** from console, but not from a menu. That is what I want.
To not have to open a console just to open up Gimp in english.

I've been trying to find out info about it, but to no help.
Thanks to all!

---

### Post by ecobuntu on 2005-10-16
[QUOTE=Mr_J_]I have GIMP, but it's in portuguese, and it's driving me nuts having to translate and find simiral meanings in the things I have to do.

So I can use **[COLOR="Olive"]LC_ALL=en_EN Gimp[/COLOR]** from console, but not from a menu. That is what I want.
To not have to open a console just to open up Gimp in english.

I've been trying to find out info about it, but to no help.
Thanks to all![/QUOTE]

What if you add an entry to you GNOME menu with that as your command?

---

### Post by seldenthuis on 2005-10-16
If you put 'export LC_ALL=en_EN' in /etc/profile you make it a system-wide environment varaible. After a reboot (in order to reload /etc/profile) Gimp should be in English.

---

### Post by objorkum on 2005-10-16
Is it just GIMP?

Open a terminal and type "env|grep LANG". What does it say?

---

### Post by Mr_J_ on 2005-10-16
```
LANG=pt_PT.UTF-8
LANGUAGE=pt_PT:pt:pt_BR:en_GB:en
```

and I just want to make GIMP start in english.
I don't really mind the rest of it in Portuguese.

---

### Post by Mr_J_ on 2005-10-20
I only want to have GIMP in english, not the entire system.
If I put it in the menu and open it the result is nothing happens.

---

