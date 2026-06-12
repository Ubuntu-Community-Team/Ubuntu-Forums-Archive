---
title: "Removed bluetooth from Kernel but he's still trying to load it."
date: 2014-12-10
forum: General Help
---

### Post by pgib8 on 2014-12-10
I removed all networking through "make menuconfig". Then built the Kernel and booted it. First I was getting a udev socket error and nothing worked. I fixed that once I enabled support for UNIX DOMAIN SOCKETS under NETWORK DEVICES.
Now the thing boots up all the way to the desktop. During boot however, it frantically continues trying to load the bluetooth stuff.

So I removed bluetooth from the kernel, so some bluetooth stuff must still be in existence. I didn't modify rootfs. Could there be something still wanting to load the bluetooth daemon?

This is my disconnect: I remove a built-in module from the kernel. Is that all I have to do or is there a file that I need to edit on the root-file-system as well?

Just for the record, I will never be using bluetooth on this device, so I want to completely get rid of it.

Many thanks in advance!

---

### Post by ajgreeny on 2014-12-10
You can search for bluetooth using synaptic, which you may have to install first, and remove it as well as several of the other bluetooth and bluez packages, but take great care to note what other packages will also be removed with them, as one or two of those are needed for some of the main packages of the desktop you are using.

However you can probably more easily stop bluetooth by installing boot-up-manager, package name **bum**, and use that to stop bluetooth from starting at boot.

---

### Post by pgib8 on 2015-02-19
I may have removed bluetooth from the Kernel but they may have been built as modules and most certainly were still inside the rootfs. During the boot process bluetooth was still being attempted to be loaded and also creating errors now. I came to the realization that when building a Linux, you don't want to remove things that you don't need, but you want to start with a blank rootfs and add things that you do need. So I used buildroot to create a nearly blank rootfs. And that's how I was able to completely get rid of bluetooth lol.
In Windows I have executables, and I can run an utility like msconfig and easily see what gets started or not. In Linux this seems to be much more complicated. I'm still overwhelmed with all this, but I just keep learning :)

---

