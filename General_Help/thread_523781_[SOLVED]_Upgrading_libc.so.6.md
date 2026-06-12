---
title: "[SOLVED] Upgrading libc.so.6"
date: 2007-08-12
forum: General Help
---

### Post by init1 on 2007-08-12
It seems like every app I run needs libncurses.so.5, which in turn needs libc.so.6. The version that I use on TTY linux is old. I cannot simply delete the old version and replace it with the one in Ubuntu, because the startup then hangs. How should I deal with this? It works if I chroot my Ubuntu partition, but that is only temporary solution.

---

### Post by Matt Yun on 2007-08-12
So, your question is about this:  [ttylinux]("http://http://www.minimalinux.org/ttylinux/showpage.php?pid=1").  Looks like a cool minimalist distro that uses the Arch Linux pacman package manager.

You will probably have to compile libc yourself; the source package build system is described on the [ttylinux package management]("http://www.minimalinux.org/ttylinux/showpage.php?pid=4") page.  It seems that ttylinux compiles their binary packages from a Slackware 10.0 environment.

---

### Post by init1 on 2007-08-12
> **Matt Yun said:**
> So, your question is about this:  [ttylinux]("http://http://www.minimalinux.org/ttylinux/showpage.php?pid=1").  Looks like a cool minimalist distro that uses the Arch Linux pacman package manager.

You will probably have to compile libc yourself; the source package build system is described on the [ttylinux package management]("http://www.minimalinux.org/ttylinux/showpage.php?pid=4") page.  It seems that ttylinux compiles their binary packages from a Slackware 10.0 environment.
Thanks! I've never compiled a distro, but I guess I'll have to if I want to run any non-native apps on it. Do you think I could I compile it from Ubuntu?

---

### Post by init1 on 2007-08-12
Actually, I've found a newer version on the site. It's for i486, but that shouldn't be a problem for me.

---

### Post by init1 on 2007-08-12
The newer version has a better libc, so I guess it's not an issue any more. But I do know now that I should recompile in order to fix such issues. Thank you!

---

