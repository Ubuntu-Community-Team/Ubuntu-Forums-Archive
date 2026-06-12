---
title: "Initial ramdisk (initrd) Questions"
date: 2007-07-16
forum: General Help
---

### Post by giacomo on 2007-07-16
Hi all,
I don't like to post immediatly without making some search and experiments.
Searching for this argument I've found fragmented informations in different kernels howto, but I was unable to locate a specific **Initial Ramdisk HOWTO**.
I've started my kernel customization process using the currently working config file (picked from the /boot directory and saved as .config in /usr/src/linux). Then I've compiled and installed the kernel with the following commands:

```

$ sudo -i
$ make-kpkg clean
$ make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image
$ dpkg -i linux-headers-2.6.20.3-*.deb
$ dpkg -i linux-image-2.6.20.3-*.deb

```

I'm conscious that the following line (previous line 3)
```
$ make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image
```
is responsible for initial ramdisk image creation.
Finnaly the question... So why the system installed kernel as ramdisk of just 6.6 MB, and one I've created is a lot bigger: 41.2 MB? (they are originated from the same kernel configuration file, after all)

I've seen that my system has a directory named **/etc/mkinitrd** with a file named **mkinitrd.conf**. Is this file directly connected with the initrd image creation? If yes, where is documented?

Thanks in advance.

---

