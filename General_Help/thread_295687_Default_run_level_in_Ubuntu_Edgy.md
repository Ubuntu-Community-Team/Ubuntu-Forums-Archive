---
title: "Default run level in Ubuntu Edgy"
date: 2006-11-08
forum: General Help
---

### Post by edrappin on 2006-11-08
To have my matlab license start up at boot time I need to know the default run level. This is usually in the inittab file but this file no longer exists in Edgy.

Your help is appreciated.

---

### Post by Jussi Kukkonen on 2006-11-08
The default is runlevel 2

---

### Post by ciscosurfer on 2006-11-08
Edgy now uses [Upstart]("http://upstart.ubuntu.com")

The directory **/etc/event.d** is where you want to look now.  You can learn more about the replacement of inittab [here]("http://www.ubuntuforums.org/showthread.php?t=269850&highlight=inittab") and [here]("http://www.ubuntuforums.org/showthread.php?t=277507&highlight=inittab").

And yes, it's still runlevel 2 at boot time.

---

### Post by edrappin on 2006-11-08
Thanks a bunch folks.

---

