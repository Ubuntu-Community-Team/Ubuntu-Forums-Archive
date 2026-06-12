---
title: "Auto-mounted Icon Problem"
date: 2007-06-29
forum: General Help
---

### Post by tntcoda on 2007-06-29
Hi,

I'm using KDE on the latest ubuntu, and i have added to remote points to fstab, i accidentally added the auto option, which I have now removed. However the automounter automounted the shares and added 2 icons to the desktop for them, I need to remove these icons. 

I have removed the auto option from fstab, and unmounted them but still the icons remain, they point to the mount points but i cannot seem to remove them. They are not listed in ~/Desktop at all, no visible links e.t.c, so i assume the automounter service has placed them there somehow?

If i try to delete them, it attempts to delete the mount point.

[IMG]http://img514.imageshack.us/img514/7762/picri0.jpg[/IMG]

Any ideas?

---

### Post by dchristo88 on 2007-08-30
Hi,

I'm having the same problem.  I have many mount points accommodate the plethora of network shares we have here.  My desktop is a mess with all these links. 

If anyone knows how to deal with this situation I'd appreciate some help.

Thanks,
D

---

### Post by dushkal on 2007-09-13
You can try starting configuration editor:

type in a console gconf-editor (or by pressing alt-f2)
browse to apps -> nautilus > desktop
and try to uncheck the volumes_visible variable.

This will however make all the volumes unvisible, you might not be able to see the CD mounted on desktop (a nice to have feature)

---

### Post by mmasic on 2007-09-14
> **dushkal said:**
> You can try starting configuration editor:

type in a console gconf-editor (or by pressing alt-f2)
browse to apps -> nautilus > desktop
and try to uncheck the volumes_visible variable.

This will however make all the volumes unvisible, you might not be able to see the CD mounted on desktop (a nice to have feature)

In KDE?
Not working for me!
Any other ideas for Kubuntu?
Thnx in advance

---

