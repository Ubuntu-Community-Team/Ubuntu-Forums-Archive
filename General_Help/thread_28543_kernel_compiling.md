---
title: "kernel compiling"
date: 2005-04-20
forum: General Help
---

### Post by dresnu on 2005-04-20
This my first experience compling a kernel the debian way. I followed line by line the instructions found on this page [http://www.ubuntulinux.org/wiki/KernelCompileHowto](http://www.ubuntulinux.org/wiki/KernelCompileHowto). Everything went ok except i can't boot the new kernel because I can't find what initrd to put in grub. The FAQ says that there should be an initrd automatically generated(?) but after installing the kernel with dpkg -i kernel-image-2.6.8.1_custom.1.0_i386.deb I can find the new kernel settings in grub but the initrd line is missing! What am I doing wrong?

Thanks!

---

### Post by dresnu on 2005-04-20
Ok, I found the solution here: [http://www.ubuntuforums.org/showthread.php?t=9807&highlight=mkinitrd](http://www.ubuntuforums.org/showthread.php?t=9807&highlight=mkinitrd)

---

