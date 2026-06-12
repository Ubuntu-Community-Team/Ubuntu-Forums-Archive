---
title: "module preventing booting, causing kernel panic"
date: 2007-03-11
forum: General Help
---

### Post by Flyn on 2007-03-11
I have a problem with a specific module preventing me from booting. How should I go about removing it manually from outside Linux?
 
Thanks in advance,
 
Flyn

---

### Post by po0f on 2007-03-11
Flyn,

Do you know how to edit kernel parameters from GRUB?  Highlight the kernel you would like to boot, then press '**e**'.  Scroll down to the line beginning with "kernel" and press '**e**' again.  Now, append the following to the parameters ("<module>" being the module you do not want loaded):

```
noload=<module>
```

Press '**enter**' to exit edit mode, then press '**b**' (I think) to boot.

When you get it all booted up fine, just add an entry for the module in "**/etc/modprobe.d/blacklist**":

```
blacklist <module>
```

---

### Post by Flyn on 2007-03-12
Um, the blacklist entry is already in place, but I understand this only prevents hotplug from loading the module and other components can still cause it to load, correct me if I am wrong?

---

