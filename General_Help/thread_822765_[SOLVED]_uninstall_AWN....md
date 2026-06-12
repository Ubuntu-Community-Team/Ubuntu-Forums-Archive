---
title: "[SOLVED] uninstall AWN...?"
date: 2008-06-08
forum: General Help
---

### Post by mparker81 on 2008-06-08
i tried it out and didnt really like it... how do i uninstall it?

---

### Post by NikoC on 2008-06-08
Perhaps [this]("http://ubuntuforums.org/showthread.php?t=626049") is a solution for your problem?

Cheers

---

### Post by mparker81 on 2008-06-08
> **NikoC said:**
> Perhaps [this]("http://ubuntuforums.org/showthread.php?t=626049") is a solution for your problem?

Cheers

tired it...

```
michael@michael-laptop:~$ sudo dpkg -r awn
dpkg - warning: ignoring request to remove awn which isn't installed.
michael@michael-laptop:~$ 

```

---

### Post by Grishka on 2008-06-08
> **mparker81 said:**
> i tried it out and didnt really like it... how do i uninstall it?

how did you install it?

---

### Post by bobbob1016 on 2008-06-08
Try sudo dpkg -r avant-window-navigator
Or try removing it through synaptic, by searching for avant-window-manager

---

### Post by mparker81 on 2008-06-08
i used the synaptic method...   worked great...  thanks

---

