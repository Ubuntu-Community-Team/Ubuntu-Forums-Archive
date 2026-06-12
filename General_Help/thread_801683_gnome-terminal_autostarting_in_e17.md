---
title: "gnome-terminal autostarting in e17"
date: 2008-05-20
forum: General Help
---

### Post by GeneralHooHa on 2008-05-20
First of all, I am an Enlightenment noob. I wanted to have my terminal autostart on deskto 2 when I logged in, so I went to the "Window Remember" preferences for it, selected "Size and Position," went into "Advanced", and checked "Start this program on login." It worked, but I wanted it to remember the locks as well so I choose "Everything."

Now it autostarts on Desktop 1, isn't remembering the size, and even though I unchecked "Start this program on login" it still starts. It does not show up in the startup applications menu (and there isn't a desktop entry). After trying to fix this myself, I now have 3 other terminals doing the same thing. Any help would be appreciated, thank you!

[IMG]http://img.photobucket.com/albums/v67/Yesman07/problem.png[/IMG]

---

### Post by GeneralHooHa on 2008-05-20
Any ideas?

---

### Post by GeneralHooHa on 2008-05-22
bump

---

### Post by GeneralHooHa on 2008-05-23
bump

---

### Post by Rui Pais on 2008-05-24
Hi GeneralHooHa 
(go easy on your bumping)

About your issue. Thats a bug on enlightenment configurations settings.
Sometimes after some settings being chosen it's hard to get them away...
The only way i find to reset them was to close any enlightenment sessions (logout), go for a console (press ctrl+alt+F1), login there and do:
```
mv ~/.e/e/config ~/.e/e/config_OLD
``` 
logout, go to Login manager (Ctrl+Alt+F7), login there and e17 should create a new default set of configurations.

To make terminal start on virtual desktop 2 you must tick 'Virtual Desktop' on 'Properties to remember' instead of Docks.

hth

---

