---
title: "Remove a module before suspend?"
date: 2007-03-15
forum: General Help
---

### Post by Bastanteroma on 2007-03-15
Following the instructions on Kernel Suspend Debugging, [https://wiki.ubuntu.com/DebuggingKernelSuspend?highlight=%28suspend%29%7C%28kernel%29](https://wiki.ubuntu.com/DebuggingKernelSuspend?highlight=%28suspend%29%7C%28kernel%29)
I found this line in my dmesg.log - hash matches device ptyte.

The instructions are to remove that module before initiating suspend.

I don't know how to do that, or what that module is.  Could I safely try not loading it all? (I don't know the best way to do that either)

EDIT - Ptyte isn't a module?

f@f-desktop:~$ rmmod ptyte
ERROR: Module ptyte does not exist in /proc/modules

---

### Post by burrodomo on 2008-03-29
The original poster has probably moved on, but for anyone else who comes across this post looking for an answer about unloading modules automatically before suspend - /etc/default/acpi-support is the file you need to edit.  It is well commented.

---

### Post by strabes on 2008-03-29
```
sudo gedit /etc/default/acpi-support
```

In that file you'll find a section that looks like this:> # Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

Add the name of your module inside the quotes on the MODULES="" line.

---

