---
title: "Startup hangs since I fiddled with the Autostart programs"
date: 2015-02-27
forum: General Help
---

### Post by syerra on 2015-02-27
Is there any way I can go back to the default start-up programs cuz the ones I chose graphically in the system and start-up make my boot hang for a couple of reasons

Samba auto-reload integration
Two instances of Mdm manager, the first loads OK and the second instance fails
A third thing, I'm not at the computer right now to see the screen but 

Simply put, is there a way to reset my startup programs without reinstalling? Thank you in advance.

Running trusty with xfce

---

### Post by ajgreeny on 2015-02-27
There will be many application.desktop files in **/etc/xdg/autostart** and your own from the xfce **Settings-manager -> Session and Startup** are in your home at **~/.config/autostart** so you may be able to remove the autostarted applications causing the problem by booting to **Recovery mode** from grub, or if that doesn't work, using a live system.

---

