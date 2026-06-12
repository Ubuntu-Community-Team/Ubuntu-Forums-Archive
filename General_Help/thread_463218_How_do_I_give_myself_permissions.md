---
title: "How do I give myself permissions?"
date: 2007-06-03
forum: General Help
---

### Post by turtlepaul on 2007-06-03
I want to edit permissions to a file so I can write to it. How do I do this? Can I use a sudo command?

---

### Post by notquitemichael on 2007-06-03
depends how long you want permissions to play with the file,

if you just want to edit it once use (in terminal)

sudo nautilus

and select it and play with it, then close it down and exit the terminal so you don't acidently damage anything too important.

however if your looking to own the file so you can always alter it, once in nautilus (windows explorer for gnome.) using the above command, find the file (note it'll open you in /root, you'll need to be in /home/username) right click, choose properties and select permissions, just change yourself to the owner and give your self read-write permissions.

hope that helps :)

---

