---
title: "Gutsy as a guest in User-Mode Linux?"
date: 2007-11-10
forum: General Help
---

### Post by Adam Atlas on 2007-11-10
I'm trying to use Gutsy as a guest OS under User-Mode Linux. Just for reference, I'm trying it with a fresh (debootstrap-based) Ubuntu install, and the precompiled [2.6.23 kernel](http://user-mode-linux.sourceforge.net/linux-2.6.23.bz2) provided on the UML homepage. The host system is also Gutsy, running an Ubuntu-provided 2.6.20 kernel.

Now, I have gotten a few other systems to work perfectly fine as guests, including Fedora Core 5 and Debian 3.1, and with the same kernel I'm trying to use for Ubuntu. But trying to run this Ubuntu system (which I built with a modified version of [this script](http://eggdrop.ch/texts/uml/) for Debian), I absolutely can't get it to a simple login prompt. When I boot one of the other distros, it behaves exactly as I'd expect -- it goes through the various boot stages and then brings me to a login prompt. With Ubuntu, it boots, but then instead of showing me a login prompt, it starts endlessly printing xterm error messages (xterm_open: $DISPLAY not set. / Failed to open console 1, err = -19) I tried some of the numerous [other I/O options](http://user-mode-linux.sourceforge.net/old/input.html), but none of them worked any better -- besides, it worked fine with the other distros, with no xterm involved anywhere.

Any thoughts?

---

