---
title: "cant install updates"
date: 2008-02-09
forum: General Help
---

### Post by hotroddude on 2008-02-09
hey again everyone,
im having an issue trying to install some new updates and it saying  this 


It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

so i do the sudo thing the in a terminal and it says this.

After unpacking 11.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)'
in the drive '/cdrom/' and press enter


i dont have a disk, how do i fix this?

thanks in advance
-steven

---

### Post by pointone on 2008-02-09
```
sudo gedit /etc/apt/sources.list
```

Delete or simply comment out the line for the CD ROM, then save, quit, and try again.

You can also do this in Synaptic by opening the "Repositories" or "Software Sources" dialog and unchecking the line for the CD ROM, but I forget how to get there... I never use it.

---

