---
title: "How do I get rid of unwanted Windows(?) files?"
date: 2015-01-16
forum: General Help
---

### Post by KayeNg on 2015-01-16
Hi guys.  I'm not sure about this but when I first installed Lubuntu in another partition of my hard disk, I think the "Used" space for that partiton was 2.70+ GB, meaning Lubuntu occupied 2.70+ GB on my fresh partition.  After I attempted to install Photoshop via playonlinux, the "Used" space jumped to 7.71 GB, and that is even when I uninstalled playonlinux and Wine.  I suspect the additional files playonlinux was downloading and installing remained on the system.  Am I wrong?

If I'm corrrect, how do I get rid of them? (I figured I'd use Gimp instead of Photoshop.)

Thanks guys.

---

### Post by Mark Phelps on 2015-01-16
Don't know what version of Photoshop you tried to install, but in general, Photoshop does not work on Linux, even using POL.

Depending on WHAT you installed from Photoshop, it might have installed a bunch of libraries and tools -- which might be taking up most of the extra 5GB of disk space.  Removing Wine and POL would not automatically uninstall Photoshop (I don't believe).  I'm NOT a Wine expert (as I found it, after extensive testing, to be pretty much a waste of time and space), but I've read that all the Wine stuff is under a hidden ".Wine" directory.  If you use your file browser and show hidden files and directories, you will be able to see if that is still there.

---

### Post by raptir on 2015-01-16
> **Mark Phelps said:**
> Don't know what version of Photoshop you tried to install, but in general, Photoshop does not work on Linux, even using POL.

Depending on WHAT you installed from Photoshop, it might have installed a bunch of libraries and tools -- which might be taking up most of the extra 5GB of disk space.  Removing Wine and POL would not automatically uninstall Photoshop (I don't believe).  I'm NOT a Wine expert (as I found it, after extensive testing, to be pretty much a waste of time and space), **but I've read that all the Wine stuff is under a hidden ".Wine" directory**.  If you use your file browser and show hidden files and directories, you will be able to see if that is still there.

Just to clarify, the .wine directory is going to be in your home folder.

---

### Post by Impavidus on 2015-01-16
Also, after uninstalling wine there may still be some dependencies of wine left on your system. You can autoremove them using the package manager.```
sudo apt-get autoremove --purge
```or use the GUI tools.

---

### Post by oldos2er on 2015-01-17
If you're positive you no longer want Wine on your system at all, open a terminal (Ctrl-Alt-t) and run ```
rm -rf .wine/
``` If you're unsure, use your favorite GUI file manager to move the ~/.wine/ folder to trash (but it will still take up disk space).

---

### Post by KayeNg on 2015-01-18
thanks a lot guys!

---

