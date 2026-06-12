---
title: "Reloading xorg.conf"
date: 2007-03-10
forum: General Help
---

### Post by Jmccaffrey on 2007-03-10
Is there a way to reload xorg.conf without restarting X or rather, exiting any of my programs?  Something similar to on windows and mac where you can simply change resolutions without having to restart anything.

---

### Post by isecore on 2007-03-10
AFAIK there's no way to reload xorg.conf while running "hot" (i.e. with X loaded).

The only way to load a configuration after you've modified it is to log out and restart GDM. Alternately you can be nasty and force a restart of X with ctrl-alt-backspace.

---

### Post by strabes on 2007-03-10
You can't reload video settings without restarting afaik, but you can tweak synaptics touchpads "live." [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

---

### Post by motin on 2008-01-26
I see you started two threads on the same subject, but for cross-reference purposes: Yes it is certainly possible, the trick is to change your xorg.conf then start a new X session on the fly - it will use the new configuration.  I just wrote a Howto on this: [http://ubuntuforums.org/showthread.php?p=4211618](http://ubuntuforums.org/showthread.php?p=4211618)

---

