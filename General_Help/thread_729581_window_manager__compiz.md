---
title: "window manager / compiz"
date: 2008-03-20
forum: General Help
---

### Post by krsgypsy on 2008-03-20
i just upgraded from ubuntu 7.04 to gusty.  it seems i have lost my windows borders. how do i get the window manager "compiz" to register a configuration tool?  i tried to open the system>preferences>windows tab but i get the message:

Window manager "compiz" has not registered a configuration tool

any ideas?

---

### Post by DjBones on 2008-03-20
have you tried going through synaptic and getting the package compizconfig-settings-manager ?
or you can gain it by opening a terminal and typing:

```
sudo apt-get install compizconfig-settings-manager
```

you might also need the emerald window decorations manager .. which you can search for in the synaptic package manager,
if its still hastling you with decorations, you can try running the command from the run dialog (alt+f2 by default i think?)

```
emerald --replace
```

hope that helps!

---

### Post by krsgypsy on 2008-03-20
i got the emerald manager and it works when i type "emerald --replace" but as soon as i close the terminal. the effects also go away.  is there a way i can make them permanent?

---

### Post by krsgypsy on 2008-03-27
its working now.  thanks for your help.

---

