---
title: "New update, gnome-terminal-data, ask to remove gnome-terminal and ubuntu-desktop"
date: 2006-08-18
forum: General Help
---

### Post by ehoffman on 2006-08-18
I just received an upgrade notice for gnome-terminal-data.  It ask me to remove gnome-terminal and ubuntu-desktop.  What about it?

Thanks.

---

### Post by givré on 2006-08-18
Did you block some of your package?

---

### Post by ehoffman on 2006-08-18
I found the problem.

I installed Xgl/Compiz, and then, removed it (for some reason, Compiz crash after a minute, and kick me back to a plain Xgl desktop, i.e. no title bar, can't move window, ...).

Though, I still had Xgl/Compiz repository.  I removed them from my sources.list and after apt-get update, that gnome-terminal-data no longer require an upgrade.  Looking at Synaptic, it's back to 2.14.2-0ubuntu1 (from 2.14.2-0ubuntu3).

Thanks for leeding me to my repository file!

Regards

Eric

---

### Post by givré on 2006-08-18
That was unexpected ;)

---

### Post by PriceChild on 2006-08-18
Yeah i've just been having a problem with the gnome terminal and compiz repos: [http://ubuntuforums.org/showthread.php?t=238790](http://ubuntuforums.org/showthread.php?t=238790)

---

