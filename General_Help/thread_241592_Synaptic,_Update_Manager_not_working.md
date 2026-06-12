---
title: "Synaptic, Update Manager not working"
date: 2006-08-22
forum: General Help
---

### Post by AirRaven on 2006-08-22
I've been getting problems with loading Synaptic and choosing to download and install updates via the graphical method- apt-get and aptitude still work perfectly, so there's no problem there.

When I try and load Synaptic, I get the following error:
```
stelhan@stelhan-desktop:~$ gksu synaptic
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory

```
I can load the update manager window, but when I choose to install the updates, the program simply goes back to the "building dependency tree" stage- it's as if the program's restarted itself.

---

### Post by h00s on 2006-08-22
[http://www.ubuntuforums.org/showthread.php?t=239238](http://www.ubuntuforums.org/showthread.php?t=239238)

---

### Post by AirRaven on 2006-08-22
> **h00s said:**
> [http://www.ubuntuforums.org/showthread.php?t=239238](http://www.ubuntuforums.org/showthread.php?t=239238)

Thanks a lot- that worked perfectly.

---

