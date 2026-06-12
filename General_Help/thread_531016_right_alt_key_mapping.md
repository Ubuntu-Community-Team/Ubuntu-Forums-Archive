---
title: "right alt key mapping"
date: 2007-08-21
forum: General Help
---

### Post by Stochastic on 2007-08-21
Hi, I just recently had compiz fusion konk out on me (every time it would go to screensaver it wouldn't wake up again) so now I'm back to regular gnome.  Everything works great now except for the right alt key.  I can't seem to get it to function as an alt key anymore, any suggestions?  I've bumped into this problem before and there was always an easy fix but I can't seem to remember what.

---

### Post by Chymera on 2007-08-21
go to the keyboard configuration under system and set your keyboard model to what it should be.... or reconfigure your x altogether (recommended) 
close x then run ```
sudo dpkg-reconfigure xserver-xorg
```
i got a similar problem with the super key and reconfiguring x worked for me

---

### Post by Stochastic on 2007-08-22
what's the simplest way to close x and not have it automatically reopen?

---

### Post by Chymera on 2007-08-22
"sudo /etc/init.d/gdm stop" or kdm if you use kde

---

