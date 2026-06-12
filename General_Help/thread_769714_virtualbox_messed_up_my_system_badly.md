---
title: "virtualbox messed up my system badly"
date: 2008-04-26
forum: General Help
---

### Post by anathema415 on 2008-04-26
Ubuntu Hardy
AMD 64x2 3800+
Nvidia GeForce 6150se
1g ram


I installed virtualbox from the add/remove hardware, then the kernel modules from synaptic. Had to restart and now it will only run in low-graphics mode, with no sound. I uninstalled all the vbox stuff but it's still messed up.
Someone please walk me through fixing this.

---

### Post by anathema415 on 2008-04-26
bump. Someone please help

---

### Post by jkratze1 on 2008-04-26
At a terminal build the kernel modules using the command sudo /etc/init.d/vboxdrv setup.  I am using virtualbox on 8.04, built the modules in this way, and everything is working.  

Good luck.

---

### Post by anathema415 on 2008-04-26
sudo: /etc/init.d/vboxdrv: command not found

Also, I removed vbox. It's my system that's completely messed up. Not a guest OS

---

### Post by nquinnathome1 on 2008-04-27
I had this same problem, running a GeForce 6600; three times I've reinstalled Hardy to attempt to find the problem, which I narrowed down to occurring when I installed any version of Virtualbox.

First of all check your kernel - your GRUB menu will tell you which one it is; probably 2.6.24-16-generic - if it is keep reading.

jkratze1 is on the right track; open your terminal (depending on whether you can still get GUI or not, you might have to enter recovery mode at the GRUB menu to get a root terminal) and run:

```
apt-get install virtualbox-ose-modules-2.6.24-16-generic
```

If you've removed Virtualbox you may as well put it back too..

```
apt-get install virtualbox
```

Then reboot
```
reboot
```

and let us know whether you've had any success.

---

### Post by sempsteen on 2008-04-27
Thanks, it worked for me.
Is it safe to remove virtualbox-ose-modules-2.6.24-16-386 and delete any lines regarding to this package from /boot/grub/menu.lst?
And what if any kernel update occurs? Do we need to install specific virtualbox module each time?
Thanks again.

---

### Post by nquinnathome1 on 2008-04-27
> **sempsteen said:**
> Thanks, it worked for me.
Is it safe to remove virtualbox-ose-modules-2.6.24-16-386 and delete any lines regarding to this package from /boot/grub/menu.lst?
And what if any kernel update occurs? Do we need to install specific virtualbox module each time?
Thanks again.

Don't remove any lines from your GRUB menu; nothing to do with Virtualbox is in there. As for the virtualbox-ose-modules-2.6.24-16-386, I would assume it's safe to remove because you're running the generic kernel module.

---

### Post by anathema415 on 2008-04-27
Thanks for the help guys. It worked!

---

