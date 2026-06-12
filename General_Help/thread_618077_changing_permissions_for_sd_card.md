---
title: "changing permissions for sd card"
date: 2007-11-20
forum: General Help
---

### Post by bladednuisance on 2007-11-20
I have a sd card that I just started using for a new device, after copying my files then sticking it into the device, it is locked I have no permissions to it, and I cant change them through the regular properties dialog, or through the device...

How can I change the permissions for my card so that I can continue to add/delete files?

---

### Post by PatrickFisher on 2007-11-20
> **bladednuisance said:**
> I have a sd card that I just started using for a new device, after copying my files then sticking it into the device, it is locked I have no permissions to it, and I cant change them through the regular properties dialog, or through the device...

How can I change the permissions for my card so that I can continue to add/delete files?

I'm going to assume that the card itself is not locked.

Try navigating to the card in the terminal and running "sudo chmod 777 -R *" (make sure you're in the right directory!!)

---

