---
title: "Kernel Build Appears to Overwrite Edited Kernel Config"
date: 2013-06-12
forum: General Help
---

### Post by buzzingrobot on 2013-06-12
I'm having a problem building one of the Ubuntu kernels.

When I edit .config to make a single change, and then begin the build, the timestamp on .config is changed to that specific time and my edit is ignored.  Examing the file shows my edit edit has been reverted.

I believe a new .config file is created and overwrites my edited file. At least, that appears to be happening.

Presumably, I'm doing something wrong.  How can I get this .config edit to stick?

Here's the command I'm using for the build:

"sudo  make-kpkg --initrd --jobs 8 --append_to_version +igd kernel_image"

---

### Post by tgalati4 on 2013-06-13
It's been a while since I rolled my own kernel, but you don't edit the .config file directly, you use the kernel-configurator which will step through the kernel options.  Once you have done that, the .config file should reflect your changes.

---

### Post by buzzingrobot on 2013-06-13
Thanks.  I used menuconfig and was able to make my little one-character edit work.

I was trying to install 13.04 on a Macbook Pro 8,2 using this: [http://blog.tkassembled.com/364/intel-graphics-on-a-2011-macbook-pro-in-linux/](http://blog.tkassembled.com/364/intel-graphics-on-a-2011-macbook-pro-in-linux/), which has you simply editing .config.

The problem with the 8,2 is not installing Ubuntu.  The problem is convincing it to use the onboard Intel video, not the Radeon chip, which runs hot with maxed out fans.

---

