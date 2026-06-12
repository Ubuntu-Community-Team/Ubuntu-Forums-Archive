---
title: "[SOLVED] URGENT &amp;quot;ldconfig deferred processing now taking place&amp;quot; does not end"
date: 2008-06-16
forum: General Help
---

### Post by editrix on 2008-06-16
This is bug 156041 on Launchpad. Lots of very technical discussion I don't understand, but my immediate problem is, I don't know what to do.

Synaptic looks like a terminal--something I haven't seen in 3 years on K/Ubuntu, and it's stuck. Can I close it?

One poster on Launchpad says he killed gksu. But I don't have gksu as a running process.

---

### Post by ChameleonDave on 2008-06-16
Type this into a terminal:

```
sudo killall synaptic
```

Killing "gksu" would work if you had started Synaptic from GNOME.  I suspect that you started it from KDE, so "kdesu" is the process that gave it admin powers.  Either way, it makes more sense just to kill Synaptic directly.

---

### Post by editrix on 2008-06-17
> **ChameleonDave said:**
> Type this into a terminal:

```
sudo killall synaptic
```

Thanks for this. I was afraid to turn the computer off, in case something was severely broken. But this a.m., it seems to be okay.

> Killing "gksu" would work if you had started Synaptic from GNOME.  I suspect that you started it from KDE

Yes, I did.

---

### Post by nickleus on 2008-10-08
> **ChameleonDave said:**
> Type this into a terminal:

```
sudo killall synaptic
```Killing "gksu" would work if you had started Synaptic from GNOME.  I suspect that you started it from KDE, so "kdesu" is the process that gave it admin powers.  Either way, it makes more sense just to kill Synaptic directly.
i had to kill this process:
> root     16074  1.2  4.9 188936 102912 ?       Ss   11:09   0:28 /usr/bin/python2.5 /usr/bin/update-manager --dist-upgrade

like this:
```
sudo kill -9 16074
```

---

