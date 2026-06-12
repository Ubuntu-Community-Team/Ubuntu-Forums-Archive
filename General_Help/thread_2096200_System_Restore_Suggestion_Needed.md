---
title: "System Restore Suggestion Needed"
date: 2012-12-19
forum: General Help
---

### Post by ajukilibodin on 2012-12-19
Hello,

I have hybrid graphics on my laptop. And for some odd reason; installation of the AMD drivers don't always work. It returns blackscreen after reboot and I can't go back even after replacing it with the old xorg.conf. So I want to know if I can perform a system restore afterwards in case of failure?

---

### Post by The Spectre on 2012-12-19
I am not sure of a System Restore function but this program will allow you to make a Image of you Hard Drive.

Redo Backup & Recovery
[http://redobackup.org/](http://redobackup.org/)

This is what I use before I do anything on my Computer that might prevent it from booting.

Plus I make weekly Images just to back up my system in case something unexpected happens.

---

### Post by Rexilion on 2012-12-19
You can always get back into your system by using a LivCD. Then chroot into the Ubuntu installation. You are able to perform all the things you are used to from the commandline.

The only limitations are if you are using different kernels. Because you are relying on the kernel of the 'live' environment. By chrooting, everything else is relying on the library's of your Ubuntu installation.

When you chroot, you could undo the ati driver installation or disable it. Aptitude and friends should work.

Need help with that?

---

### Post by ajukilibodin on 2012-12-19
I am looking for a way to revert the AMD drivers and all the configuration files they changed in case it's needed. So I'm not sure what my options are. What would you suggest?

---

### Post by Rexilion on 2012-12-20
Well, as before: chroot into the installation with the liveCD. Which goes something along the lines of this:

- boot liveCD
- open a terminal
```
mkdir /mnt/chroot
mount /dev/sda1 /mnt/chroot
mount -t proc none /mnt/chroot/proc
mount -t sysfs none /mnt/chroot/sys
mount -o bind /dev /mnt/chroot/dev
chroot /mnt/chroot /bin/bash
```

Replace /dev/sda1 with your actual live '/' (root) filesystem.

You are now chrooted. To uninstall fglrx: Do in the chroot (something along the lines of):

```
dpkg --purge fglrx fglrx-amdcccle fglrx-amdcccle-updates fglrx-control fglrx-updates
```

---

### Post by Mark Phelps on 2012-12-20
> **ajukilibodin said:**
> ...So I want to know if I can perform a system restore afterwards in case of failure?

Sorry, Ubuntu does not have anything similar to System Restore that is offered in Windows.

---

