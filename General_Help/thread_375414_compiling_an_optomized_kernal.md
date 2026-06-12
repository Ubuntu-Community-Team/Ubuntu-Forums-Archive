---
title: "compiling an optomized kernal?"
date: 2007-03-03
forum: General Help
---

### Post by rabid9797 on 2007-03-03
hey guys. i want to compile an optimized kernal for my specific hardware in ubuntu. currently im running 2.6.17-11-generic

can someone suggest a guide or how to thread on how to optimize this/a kernal? (i already tried the thread suggested in ubuntuguide.org but it was for 2.6.16)

---

### Post by rabid9797 on 2007-03-03
OK, another question, can i use the 2.6.20.1 kernal with ubuntu? i found a guide to compiling but i don't know if its safe...

---

### Post by DagMan on 2007-03-03
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)
That says dapper but it works fine on edgy and feisty as well.
I recommend using the kernel source from the ubuntu repos and making your selections from there, it will  have ubuntu specific patches.  Ubuntu really is well patched for added hardware support as well.

If you're compiling a 2.16.17 kernel from ubuntu sources for dapper or a  2.6.20 from feisty on a dapper or edgy machine, download the deb for an image file too and use the archive manager to extract the config file out of the /boot directory in the archive. Use that file for a config file instead of using a current one that is for a lower version of the kernel.  That would be at the step that says cp /boot/config-`uname -r` ./.config   You would copy the extracted config file to ./.config instead

This link will let you search dapper edgy and feisty packages, just select the right one.  You can then download the kernel-source and a kernel image if you want to get the config file that would be used natively. [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)

I have btw had the 2.6.20 kernel work for me just fine.  I used it from the above link on Dapper if I remember correctly.  It was a large compile and the compiled source was close to 2 gigs so if you've partitioned /usr/src separately make sure you have room or build it elsewhere.  2.6.20 has an option for core 2 duo if you have that processor as well.  Apart from that, I don't know what the advantage would be.

At the step, make menuconfig, select what you want, deselect what you want.  The most important part for me is processor type and features.

---

