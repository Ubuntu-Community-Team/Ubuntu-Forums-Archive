---
title: "Load nvidiafb instead of nvidia if in single mode"
date: 2007-09-23
forum: General Help
---

### Post by Keyper7 on 2007-09-23
Hi, I think the title kinda says it all...

Is there any way I can make the system automatically detect if it's running in single mode
or not and load a different set of modules depending on the answer?

I know nvidia and nvidiafb don't go well together, but since I don't have use for the nvidia
module while in single mode, I would like to have nvidiafb for a nice framebuffer console. :)

If other words, I just want to know if something simple like

if(single mode){
  rmmod nvidia
  modprobe nvidiafb
}

is possible.

---

### Post by ddrichardson on 2007-09-24
Not too sure, to be honest, but couldn't you use a different kernel configuration as a single user mode from grub?

---

