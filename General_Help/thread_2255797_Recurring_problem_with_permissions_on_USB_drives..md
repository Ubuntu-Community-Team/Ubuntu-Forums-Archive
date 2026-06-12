---
title: "Recurring problem with permissions on USB drives."
date: 2014-12-07
forum: General Help
---

### Post by RayArdia on 2014-12-07
I have a similar recurring problem with permissions on USB drives, it seems that whenever I think I've sorted it out, I once again find that I can't edit usb devices and get 'read-only file system'.
Latest attempt is to get _permanent_ control ie full read/write access to an Intenso 8GB Music Walker.
I have tried 'chown ray:ray /media/ray/Intenso'  and  'chmod 777 ray:ray /media/ray/Intenso'  without any success. 

Gparted shows this:-
[ATTACH=CONFIG]258449[/ATTACH]

Device 'Properties', 'Permissions', 'Change Permissions' shows:-
[ATTACH=CONFIG]258450[/ATTACH]
but when I attempt to (eg) delete a file I'm still stuck! - 'read-only'

How do I make these USB devices do what I want, ie allow me read/write access as soon as they are plugged in?

---

### Post by coffeecat on 2014-12-07
Moved to own thread.

---

