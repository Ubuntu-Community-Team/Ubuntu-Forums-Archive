---
title: "Lubuntu 18.10 Auto login?"
date: 2019-04-04
forum: General Help
---

### Post by jazz53 on 2019-04-04
Hi; 
How do I get Lubuntu to automatically log me in on start?
After doing some reading I have edited sddm to read as folllows

[Autologin]
user=Al
Session=Lubuntu

But I still can not get it to log in at start or reboot.
Login still opens and asks for password.

TIA

---

### Post by Dennis N on 2019-04-05
The trick is you have to add .desktop to the Session name:

```
[Autologin]
Session=lxqt.desktop
User=dragonslayer
```

This works.

---

### Post by jazz53 on 2019-04-06
Well,,,, HMM.
I tried to change this and got

/etc/sddm.conf: command not found

Got fed up and did a complete re-install
This time I found the automatically login box.
After I went to check and see what the difference is and still get

/etc/sddm.conf: command not found.

Not sure if this QT stuff is ready for prime time.

---

### Post by Dennis N on 2019-04-06
> /etc/sddm.conf: command not found
This by itself is not a command; just the file you need to edit. You need to open this file in a text editor. I suggest using the following command in the terminal to launch the nano text editor:

```
sudo nano /etc/sddm.conf
```

use keyboard to navigate to the line to edit. Fix it, then ctrl+o to save, and ctrl+x to quit and return to terminal prompt.

---

