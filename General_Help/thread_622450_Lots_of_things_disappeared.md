---
title: "Lots of things disappeared"
date: 2007-11-24
forum: General Help
---

### Post by nandorj78 on 2007-11-24
Hi, I messed big time playing a bit with the synaptics or whatever it is called. I removed things I shouldn't have removed in the System Menu, including the ' software source'  and the synaptics manager itself. How do I fix it? Is there a sort of system restore to undo the changes?

thanks!

---

### Post by aysiu on 2007-11-24
> **nandorj78 said:**
> Hi, I messed big time playing a bit with the synaptics or whatever it is called. I removed things I shouldn't have removed in the System Menu, including the ' software source'  and the synaptics manager itself. How do I fix it? Is there a sort of system restore to undo the changes?

thanks!
Press Alt-F2 and type ```
gnome-terminal
``` (hopefully you haven't removed that!)

Then, in the terminal, paste this command: ```
sudo apt-get update && sudo apt-get install ubuntu-desktop
``` That should give you everything default back.

---

