---
title: "[SOLVED] virtual box in Ubuntu 8.04"
date: 2008-05-28
forum: General Help
---

### Post by cosine352 on 2008-05-28
Hi All,
I have installed virtual box. But when I try to START windows XP on it it gives error as below,

> 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

 

So I did 
> sudo /etc/init.d/vboxdrv setup

I got this output

> * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module
 * Look at /var/log/vbox-install.log to find out what went wrong


/var/log/vbox-install.log looks

> Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

Please help. I have some important software installed in windows xp.

Thanks

---

### Post by cosine352 on 2008-05-28
I have solved it. I did
> sudo aptitude install linux-headers-$(uname -r)


and then reinstall virtualbox

---

### Post by neur0 on 2008-05-28
It did that after a kernel upgrade, the fixed module is already in the repos, but glad you solved anyway.

---

