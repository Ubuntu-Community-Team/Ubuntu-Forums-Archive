---
title: "[SOLVED] vi editing question from new user"
date: 2007-12-06
forum: General Help
---

### Post by moonpup on 2007-12-06
Hi,

I'm new to ubuntu coming over from redhat and have a question regarding vi. In redhat, when i'm using vi to edit a file and i'm in insert mode, I am able to move around the document using the arrow keys. I have noticed when using vi in ubuntu, that if i'm in insert mode and use the arrow keys I get new lines starting with ABCD depending on which arrow key i pressed.

Does vi in ubuntu have some different key mappings that I'm not used to. Why do I have to hit escape to go to command mode to move around? Does anyone know how to remap the arrow keys so that i can move around in insert mode?

---

### Post by TurboRush on 2007-12-06
Try 
```
:set nocompatible
```

---

### Post by moonpup on 2007-12-06
I simply installed vim enhanced (vim improved) as it's not installed by default in ubuntu, but is on redhat.

---

