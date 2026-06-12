---
title: "Remove different kernels"
date: 2008-07-06
forum: General Help
---

### Post by Esahp on 2008-07-06
How do I make sure these/this two/one kernel(s) are/is removed from the system, as well as the menu.lst (obviously I can just remove them from the list)

/boot/grub/menu.lst:
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-virtual
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-virtual root=UUID=53343056-74dc-4e05-8c0a-b263f7fb105e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-virtual
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-virtual (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-virtual root=UUID=53343056-74dc-4e05-8c0a-b263f7fb105e ro single
initrd		/boot/initrd.img-2.6.24-19-virtual

```

---

### Post by scragar on 2008-07-06
they are removed from the list when you uninstall them, normaly run either manualy or if they were updated via the package manager(or update manager) with```
sudo apt-get autoremove
```

to manualy pick the one to remove use```
sudo apt-get remove linux-headers-**VERSION***
```

---

### Post by Esahp on 2008-07-06
It appears to already be uninstalled, but left behind in the GRUB menu. The only reason I ask is, when I don't stop GRUB from booting the -virtual, it'll get to the GDM login screen, but not allow me to move the mouse or type anything, which is what leads me to believe it's not uninstalled.

Unless that is just normal behavior and it's piggy-backing off of something else that is malfunctioning because of it choosing -virtual. Anyway, any ideas why that is occurring?

I'll remove them from the menu.lst in a little bit if everything is ok.

Thanks for the tip so far, scragar.

```

phase@geek:~$ dpkg --list | grep linux-headers
ii  linux-headers-2.6.24-19                    2.6.24-19.34                       Header files related to Linux kernel version
ii  linux-headers-2.6.24-19-generic            2.6.24-19.34                       Linux kernel headers for version 2.6.24 on x
ii  linux-headers-generic                      2.6.24.19.21                       Generic Linux kernel headers
phase@geek:~$ 

```

---

### Post by fragos on 2008-07-06
If you like GUI better, run Synaptic Package Manager and search for 2.6.24. This will show you all the kernel versions and directly relating kernel files. Mark for removal any you no longer want and "Apply" the changes. Grub's menu.lst will automatically be updated for you.

---

### Post by Esahp on 2008-07-06
> **fragos said:**
> If you like GUI better, run Synaptic Package Manager and search for 2.6.24. This will show you all the kernel versions and directly relating kernel files. Mark for removal any you no longer want and "Apply" the changes. Grub's menu.lst will automatically be updated for you.

It appears I didn't properly uninstall it, Synaptic did show me it still on the system, and that fixed it (as well as removed it from the menu.lst)

Thanks!

---

