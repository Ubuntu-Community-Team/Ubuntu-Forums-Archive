---
title: "ubuntu doesn't start after k3b installation"
date: 2006-11-10
forum: General Help
---

### Post by vale_ron on 2006-11-10
hi, i am italiano, so i am sorry for my english... however i go immedately to my problem: i use ubuntu 6.10 with gnome and i have installed k3b. after this installation, some icons on the desktop and in the applications menu are disappeared. So, i have tried to restart my computer but, when i insert username and password, after few seconds, login screen appears again. in substance, i don't be able to start ubuntu!!!
Help me please...

---

### Post by Average Joe on 2006-11-10
Strange. I also run Ubuntu 6.10 (with Gnome) and have k3b installed. It works fine for me. However, if I were you, I would try to log in from a console screen. When you see your Ubuntu log in screen, press Ctrl+Alt+F1 to get a console window. Then log in with your username and password. Next remove k3b with:
> sudo apt-get remove k3b
Then, press Ctrl+Alt+F7 I try to log in the normal way again. Or maybe reboot if that doesn't work.

---

### Post by vale_ron on 2006-11-12
i have already tried to remove k3b but this not have functioned. any suggestion? please HELP ME!|

---

### Post by vale_ron on 2006-11-13
RESOLVED: the space in the file system was null, so the system didn't start in graphic  modality correctly. i have removed a few gb of data and all has returned to the normality.

---

