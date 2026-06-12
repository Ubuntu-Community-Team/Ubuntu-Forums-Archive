---
title: "nm-applet asking password???"
date: 2007-05-26
forum: General Help
---

### Post by tuxy on 2007-05-26
I have upgraded Ubuntu to Fiesty on my laptop. Now I get "nm-applet" keyring some thing.... asking for password continuously and I can't remember what the password is. I am not sure if I have set password before. Because of this I cant access wireless network at my place. 

Can any one tell me how to reset Network Manager (nm-applet) keyring password which goes on top right of the Gnome panel???

---

### Post by mbradlcu on 2007-05-27
I'm not sure but I think this maybe the place were the keyring stores it's keys:
/home/{your_home_dir|/.gnome2/keyrings
I would shut down the key ring manager:
```
killall -15 gnome-keyring-daemon
```
delete or better move the keyrings file and then either reboot or restart the keyring manager

---

