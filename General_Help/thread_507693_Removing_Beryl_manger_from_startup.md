---
title: "Removing Beryl manger from startup"
date: 2007-07-23
forum: General Help
---

### Post by DrClaw27 on 2007-07-23
I remote into my home machine from work with NX linux but on the weekend I setup beryl and now it disconnects me from the session as soon as I connect. I have logged in as a different user that isn't running beryl and I want to remove beryl from starting up on my primary account. Where would I do this?

---

### Post by adam_r on 2007-07-23
run gconf-editor
in Desktop --> Gnome --> Applications -->  Window_Manager
change the deafult value to /usr/bin/metacity (or k somthing for KDE)
and check in your System --> Prefrences --> Sessions that gnome-wm is there (for gnome)

---

