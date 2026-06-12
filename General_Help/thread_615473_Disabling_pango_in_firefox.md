---
title: "Disabling pango in firefox"
date: 2007-11-17
forum: General Help
---

### Post by Colro on 2007-11-17
Launching Firefox with MOZ_DISABLE_PANGO=1 *doubles* my rendering speed. Is there any way to make this option permanent so that I don't have to launch my browser from a terminal?

---

### Post by wooster on 2007-11-17
Hi there. If you want to keep that permanent just add that export to your .bashrc.  You can just use gedit and add export MOZ_DISABLE_PANGO=1  to the end of the .bashrc file in your home directory.  

If you want a simple command to run from a terminal to do it here you go

```
echo "export MOZ_DISABLE_PANGO=1" >> ~/.bashrc
```

After it's added to your .bashrc you will have to logout of your session and login in for this to work. It should remember it permanently now.

---

