---
title: "DRM software on Ubuntu"
date: 2005-07-27
forum: General Help
---

### Post by hal8000 on 2005-07-27
Will there  be a build for the Digital Radio Mondial Receiver for Ubuntu?
The sourceforge page below has source packages and rpms, but no Debian or Ubuntu builds as yet.

[http://drm.sourceforge.net/installation.html](http://drm.sourceforge.net/installation.html)

Alternatively if I compile from source, where is the best place for the binaries, /usr/local/bin or /usr/bin ? Thx in advance.

---

### Post by rwabel on 2005-07-27
[QUOTE=hal8000]Will there  be a build for the Digital Radio Mondial Receiver for Ubuntu?
The sourceforge page below has source packages and rpms, but no Debian or Ubuntu builds as yet.

[http://drm.sourceforge.net/installation.html](http://drm.sourceforge.net/installation.html)

Alternatively if I compile from source, where is the best place for the binaries, /usr/local/bin or /usr/bin ? Thx in advance.[/QUOTE]
 I think it's up to you, but I wouldn't install in /usr/bin, because there are the installed applications from "synaptic" and manually installed debs. I might get you in trouble, when having the same app in different versions.
I always install in /usr/local/bin, to differentiat my installed packages from the system one. In that case I can use for example a newer version and also and older version of an app

---

