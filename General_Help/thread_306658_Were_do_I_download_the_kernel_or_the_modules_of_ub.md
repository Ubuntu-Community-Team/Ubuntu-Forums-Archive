---
title: "Were do I download the kernel or the modules of ubuntu edgy live cd?"
date: 2006-11-25
forum: General Help
---

### Post by nadavvin on 2006-11-25
Hello

I want to create ubuntu live cd with the linux-live.org scripts,
therefore I need unionfs and squashfs support in the kernel.

Ubuntu have a live cd.

How can I get the modules from it?

I search for package of them and I get:
```

$ apt-cache search unionfs
unionfs-source - source for the unionfs driver
unionfs-utils - stackable unification file system - management tools
nadav@nadav-desktop:~$ apt-cache search squashfs
squashfs-tools - Tool to create and append to squashfs filesystems
squashfs-source - Source for the squash filesystem


```

How can I use them?

---

### Post by nadavvin on 2006-11-25
I install the packages:
```

 unionfs-source unionfs-utils squashfs-source squashfs-tools

```

how do I compile or download this modules?

```

$ sudo ./runme.sh 
Changing current directory to /tmp/linux-live-5.5.0
Linux Live scripts were installed successfuly in /
Enter path for the kernel you wanna use [hit enter for /boot/vmlinuz]: /boot/vmlinuz-2.6.17-10-generic
Creating LiveCD from your Linux
some debug information can be found in /tmp/linux-live-debug.log
copying cd-root to /tmp/live_data_25197, using kernel from /boot/vmlinuz-2.6.17-10-generic
Using kernel modules from /lib/modules/2.6.17-10-generic
creating initrd image...
The directory /tmp/linux-live-5.5.0/initrd/kernel-modules/2.6.17-10-generic doesn't exist.
Please create it and copy squashfs.ko and unionfs.ko modules
for your kernel (2.6.17-10-generic) to this directory.


```

---

### Post by nadavvin on 2006-11-25
It's ok I found what to do

---

