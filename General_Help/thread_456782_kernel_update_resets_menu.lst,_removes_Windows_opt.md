---
title: "kernel update resets menu.lst, removes Windows option"
date: 2007-05-28
forum: General Help
---

### Post by EtniesBMX on 2007-05-28
I am running a sytem with dual boot. Each time I update the kernel, the menu.lst resets itself and adds in an option for the newest kernel installed. In the process it also removes the option for Windows, making me manually edit menu.lst each time. It's consistently happening, and it seems like it may be a bug. 

Does anyone know why it keeps ignoring the windows boot option??

---

### Post by simone.brunozzi on 2007-05-28
> **EtniesBMX said:**
> I am running a sytem with dual boot. Each time I update the kernel, the menu.lst resets itself and adds in an option for the newest kernel installed. In the process it also removes the option for Windows, making me manually edit menu.lst each time. It's consistently happening, and it seems like it may be a bug. 

Does anyone know why it keeps ignoring the windows boot option??

hmm.... nothing like this happens in my systems... did you check the repos you are using? Are they official?

---

### Post by heldal on 2007-05-28
> **EtniesBMX said:**
> I am running a sytem with dual boot. Each time I update the kernel, the menu.lst resets itself and adds in an option for the newest kernel installed. In the process it also removes the option for Windows, making me manually edit menu.lst each time. It's consistently happening, and it seems like it may be a bug. 

Does anyone know why it keeps ignoring the windows boot option??

Are you sure you're not putting the windows-entry in the part of the file handled by the installer?  Look at the comments in the file and you'll find:

```

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
.
.
.
### END DEBIAN AUTOMAGIC KERNELS LIST
```


Simply do as the comments say ;)

---

### Post by EtniesBMX on 2007-10-16
> **heldal said:**
> Are you sure you're not putting the windows-entry in the part of the file handled by the installer?  Look at the comments in the file and you'll find:

```

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
.
.
.
### END DEBIAN AUTOMAGIC KERNELS LIST
```


Simply do as the comments say ;)

Ah that was the problem. Thanks.:)

---

