---
title: "Notification area trouble"
date: 2008-07-02
forum: General Help
---

### Post by kehender on 2008-07-02
Ok, so I'm sure this is covered somewhere else but I've been looking for a while and haven't been able to find exactly what I need. I've been trying to change the icons in the notification area such as pidgin's icon and banshee's. I'm using an icon theme called allergy. It changed the network manager icon, the battery icons, and possibly some others, but pidgin's and banshee's stayed default. How do I change the ones for those two? Do I have to actually change something for the notification-area or for the apps themselves? For some reason I can't find pidgin's or banshee's icon files. If someone could help or at least point me to the right post I would be very grateful. Thanks!

---

### Post by drs305 on 2008-07-02
Edited: see scragar's post. The ones below are only user icons. 

pidgin's icons are located in /home/yourusername/.purple/icons

---

### Post by scragar on 2008-07-02
you could directly edit the images if you wanted, they are stored in:
```
/usr/share/pixmaps/pidgin/
``` not sure about allergy.


Oh, and the icons in use are application specific(some applications detect the theme themselves, which is why their icons change)

EDIT:

/home/yourusername/.purple/icons is not the icons to change, thats the icons that appear next to names on MSN etc(cached versions to save downloading them again)

---

### Post by kehender on 2008-07-02
> **drs305 said:**
> pidgin's icons are located in /home/yourusername/.purple/icons
Ah, that's why I couldn't find them. I kept looking for pidgin everywhere. I forgot it was purple. Thanks!

---

### Post by kehender on 2008-07-02
> **scragar said:**
> you could directly edit the images if you wanted, they are stored in:
```
/usr/share/pixmaps/pidgin/
``` not sure about allergy.


Oh, and the icons in use are application specific(some applications detect the theme themselves, which is why their icons change)

EDIT:

/home/yourusername/.purple/icons is not the icons to change, thats the icons that appear next to names on MSN etc(cached versions to save downloading them again)
Awesome, thanks!

---

### Post by drs305 on 2008-07-02
The ones you are actually looking for are probably located where scragar told you to look. The one's in .purple/icons are pretty limited. The system icon is probably the one you are looking for and would be in /usr/share/pixmaps/pidgin.

For user settings, look in $HOME/.purple.

---

