---
title: "[SOLVED] opt directory not writeable?"
date: 2008-03-10
forum: General Help
---

### Post by iheartubuntu on 2008-03-10
Im trying to install a game called "PlaneShift" and Im getting an error message when the game tries to install to my opt directory. It says....

The directory
/opt
is not writable by the current user

I am the current and ONLY user! I tried to change settings on my opt directory but everything was greyed out. I installed this to my home/dave directory and the game doesnt work. Any tips?

---

### Post by Oldsoldier2003 on 2008-03-10
> **shirteesdotnet said:**
> Im trying to install a game called "PlaneShift" and Im getting an error message when the game tries to install to my opt directory. It says....

The directory
/opt
is not writable by the current user

I am the current and ONLY user! I tried to change settings on my opt directory but everything was greyed out. I installed this to my home/dave directory and the game doesnt work. Any tips?

try running the installation script under sudo...

```
cd directorywhere the installer is
sudo ./install
```
(or whatever the installer script is named)

---

### Post by iheartubuntu on 2008-03-10
thanks!

---

