---
title: "compiling a custom kernel"
date: 2007-06-05
forum: General Help
---

### Post by cuberoot on 2007-06-05
Hello,

I have a couple of questions about compiling custom kernels. I just got a source tree from kernel.org and wanted to build and install it. I did a make in the source directory and compied BzImage to /boot/vmlinuz. Added te image to grub.menu.lst

I didn't boot. Then I searched a bit and did this:

make-kpkg --initrd --append-to-version=-custom kernel_image
dpkg -i linux-image-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb

Then it booted.

My questions are: what is initrd and why is it needed? I also tried to simply do a make the next time and copied over the image to the last vmlinuz, again I wouldn't boot. Does it always have to be done through a package?

---

### Post by snobel on 2007-06-06
Doing it through a package is the clever way, because then you can uninstall it easily, e.g. through synaptic. Also, the .deb install will automatically update your grub menu.
There is a good kernel how-to  [here]("http://www.howtoforge.com/kernel_compilation_ubuntu"), except do 'sudo -s' to become root instead of assigning a root pw...

The initrd is the boot environment ('initial ramdisk'), a sort of linux mini-install used while devices etc. are set up.

---

### Post by cuberoot on 2007-06-07
Thanks. is there some way to not have install as a package the second time you build a kernel. For example you install an image by doing "make-kpkg...." and all that. Second time around you just want to builld bzImage and copy it over to /boot under the appropriate name (from the first  one). I tried that and it wouldn't boot. 

I am trying some modifications to the TCP code and installing everytime as a package is quite annoying (and it fills up the disk quite fast).

Thanks again.

---

