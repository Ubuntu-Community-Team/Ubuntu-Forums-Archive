---
title: "problems after just installing kde"
date: 2008-02-14
forum: General Help
---

### Post by lxtubman on 2008-02-14
Right after installing kde on my linux side. my gnome side changed a little.  

first, it tells me GDM is no longer running.

when i type gdm in the command line i get
WARNING: GDM file gdm-daemon-config.c: line 2121 (): Cannot run seteuid to 0: Operation not permitted
GDM file gdm-daemon-config.c: line 2121 (): Cannot run seteuid to 0: Operation not permitted

also when i try to shut down the shutdown button and the restart button have dissapeared. i now have to log out to shut down...

any answers to anything?

thanks!

---

### Post by p_quarles on 2008-02-14
Basically, you can't use both GDM and KDM at the same time. Either one, though, will run KDE or Gnome. If you want GDM back, you need to reinstall the package:
```
sudo dpkg-reconfigure gdm
```
Choose the GDM option when it's presented.

---

### Post by lxtubman on 2008-02-14
i tried that and i get
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

i restarted...tried again... same thing...

---

