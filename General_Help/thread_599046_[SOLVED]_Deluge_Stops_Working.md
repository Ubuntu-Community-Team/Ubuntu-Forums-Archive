---
title: "[SOLVED] Deluge Stops Working"
date: 2007-10-31
forum: General Help
---

### Post by Cochise on 2007-10-31
After i open deluge a few times it´&#314;l will stop working. I have tried reinstalling it, removing it with apt-get and even using aptitude to purge the config files, I have also tried deleting the config files in /home/cochise/.config/deluge myself. I'm using version 5.6.1.2 the latest one from the deluge&#347; website, i have also tried it using th e.deb from getdeb.net which is the same version. I have also tried using older/other version but i have the same problem with them all. I'm running Gutsy/GNOME.

Here´s the output if i run it from a terminal:

> no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Segmentation fault (core dumped)


for now I have gone back to using transmission but i prefer deluge so any help would be appreicated.

---

### Post by Cochise on 2007-11-01
Anyone have any ideas????

---

### Post by Leonivek on 2007-11-01
I'm having the same problem after updating it to the latest version today.

---

### Post by Cochise on 2007-11-01
its a nightmare, i miss it really badly

---

### Post by Cochise on 2007-11-01
Okay, went onto the deluge irc room, #deluge @ irc.freenode.net, and was helped by markybob, who spend 30 minutes helping me until he found the problem. Its an error relating to upnp in my case, it can be fixed by disabling upnp but you cant because you cant start the program  so i´ve attached my prefs.state file, copy that into /home/yourusername/.config/deluge overwriting your own config file (you will lose all your settings so make a backup of your previous file first). hope it works for you, if not check the irc above and hopefully they´ll help as much as they helped me.

---

