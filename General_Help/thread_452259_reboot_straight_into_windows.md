---
title: "reboot straight into windows"
date: 2007-05-23
forum: General Help
---

### Post by smurphs on 2007-05-23
I've been looking for a way to reboot straight from ubuntu into windows without having to stick around for the grub-menu. 

I think I've found a way with the grub-reboot command. It works, but when you come out of windows grub takes you back to windows again, unless you hang around to tell grub you want to go to ubuntu!

Does anyone know of a way around this, or am I stuck with this half solution?

For anyone who wants to use grub-reboot, you just type 

sudo grub-reboot 1

in a terminal. My windows partition is first on my hard disk, hence the 1, this is the usual setup if you've installed ubuntu from the live cd whilst keeping windows. to make it work you first have to type:

sudo gedit /boot/grub/menu.lst

and change:

default 0 (about 10 lines down), to:

default saved

also, go to the bottom and make sure you have 'savedefault' within your ubuntu menu item, also remove savedefault from you windows menu item (if it's there).

---

### Post by bernied on 2007-05-23
If you wanted to alternately boot linux and windows, you could use the savedefault grub command, something  like this:
```
title linux
root ...
kernel ...
initrd ...
savedefault 1

title windows
root ...
chainloader ...
savedefault 0
```
Check out the Automagic options as well, there may be a way to keep this during kernel upgrades.

---

### Post by veerakumar on 2007-05-23
if you can access menu.lst from windows & linux then it is possible.
Currently I know of none.
You can make custom scripts if you have knowledge.

---

