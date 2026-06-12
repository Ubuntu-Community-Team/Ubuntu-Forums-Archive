---
title: "How do I stop modprobe from loading files"
date: 2005-10-04
forum: General Help
---

### Post by Psquared on 2005-10-04
that are either missing or have been uninstalled.

specifically, when booting up modprobe tries to load a file called pciehp which does not exist. Must have something to do with hotplug because it happens right after that. It also wants to load part of Rox Zeroinstall which I have uninstalled.

---

### Post by mlomker on 2005-10-04
> It also wants to load part of Rox Zeroinstall which I have uninstalled.

You can try adding it to /etc/hotplug/blacklist but I've had mixed results with that.  Perhaps you just need to **sudo depmod -A**?

---

### Post by Psquared on 2005-10-04
[QUOTE=mlomker]You can try adding it to /etc/hotplug/blacklist but I've had mixed results with that.  Perhaps you just need to **sudo depmod -A**?[/QUOTE]

What would that do??

---

### Post by mlomker on 2005-10-04
[QUOTE=Psquared]What would that do??[/QUOTE]

Update the kernel module dependencies.  I don't know if it'd help but it can't hurt anything.

---

### Post by Psquared on 2005-10-05
[QUOTE=mlomker]Update the kernel module dependencies.  I don't know if it'd help but it can't hurt anything.[/QUOTE]

Well, guess what ... it worked. Thanks :p :)

---

