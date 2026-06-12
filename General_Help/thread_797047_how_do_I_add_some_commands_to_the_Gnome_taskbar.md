---
title: "how do I add some commands to the Gnome taskbar"
date: 2008-05-16
forum: General Help
---

### Post by agentnixon on 2008-05-16
I want to add the command 
```
sudo /etc/init.d/networking restart
```
to my Gnome taskbar. I was thinking of doing it through going to "add to panel" and "add custom application launcher" and then type in the code in the command line, but that doesn't seem to work. What am I doing wrong?

---

### Post by Gunman1982 on 2008-05-16
Instead of 'sudo' use 'gksu' so it gives you a graphical window to type in your passwort, with sudo it expects a passwort, doesn't get one, ends right away.

---

### Post by agentnixon on 2008-05-16
ah, simple mistake. Thanks!

---

