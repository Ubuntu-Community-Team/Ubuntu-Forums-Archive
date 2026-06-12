---
title: "Tar.gz xpde install"
date: 2008-06-29
forum: General Help
---

### Post by sponsoredwalk on 2008-06-29
Hi on Ubuntu 7.10 and i would like to install xpde-0.5.1 from    [http://www.xpde.com/releases.php](http://www.xpde.com/releases.php) but it is a tar.gz file and i have no clue how to install one of these files. If i were to install it in to /home/zxcv/.xpde could someone direct me in doing this...

*Also, will xpde be where the login window is, where you can select between gnome or xfe? *

---

### Post by HalPomeranz on 2008-06-30
Wow, the install on this package is very non-standard (and more than a little brain-damaged).  Anyway, here's what you're supposed to do according the the INSTALL file in the tar.gz file:

```

cd /usr/share
sudo tar zxf /path/to/your/copy/xpde-0.5.1.tar.gz

```

Apparently the command /usr/share/xpde/bin/startxpde will then start XPde.  More info in /usr/share/xpde/INSTALL once you've unpacked the tar.gz file using the "sudo tar ..." command shown above.

---

### Post by jnw222 on 2008-06-30
from now look for .deb.
that is ubuntu's main installer

---

### Post by HalPomeranz on 2008-06-30
> **jnw222 said:**
> from now look for .deb.
that is ubuntu's main installer

That isn't an option for this software.  And there's nothing in the repositories either.  I checked both before I posted my response above.

---

### Post by ShodanjoDM on 2008-06-30
It might be better if you install icewm and configure it to look like XP (or Vista) though. It's because the xpde last update was two years ago so I think you'll likely encounter more problems.

---

