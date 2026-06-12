---
title: "svgalib module + custom kernel and headers"
date: 2007-02-04
forum: General Help
---

### Post by dozier768 on 2007-02-04
Hello,

i have been racking my brain trying to get svgalib to compile cleanly with kernel 2.6.19 "vannilla patched with ck2" and it keeps die'ing when it tries to compile the kernel module, here's the output

> make[2]: Entering directory `/usr/src/linux-2.6.19ck2'
  CC [M]  /home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper/main.o
/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper/main.c:1:26: error: linux/config.h: No such file or directory
/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper/main.c:20:35: error: linux/devfs_fs_kernel.h: No such file or directory
/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper/main.c: In function ‘svgalib_helper_ioctl’:
/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper/main.c:358: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper/main.c: In function ‘svgalib_helper_open’:
/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper/main.c:446: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[3]: *** [/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper/main.o] Error 1
make[2]: *** [_module_/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.19ck2'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper'
make: *** [installmodule] Error 2


I have installed the image and headers, i have also tried passing "-I/usr/src/linux/include/" to the compiler, i cant get the dang thing to go.

i think this is the problimatic area > 
/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper/main.c:1:26: error: linux/config.h: No such file or directory
/home/dan/Desktop/svgalib-1.9.25/kernel/svgalib_helper/main.c:20:35: error: linux/devfs_fs_kernel.h: No such file or directory

oddly enough its correct..... those headers dont exist but in the stock "linux-headers-2.6.17-10".. why dont my custom headers contain this?

can i rectify this? or am i missing something due to my ineptitude? :confused: 

any help would be greatly apriceated.

---

### Post by dozier768 on 2007-02-04
forgot to mention it works perfectly well with the stock kernel and headers

---

### Post by dozier768 on 2007-02-04
well it would seem i figured it out, apparently those two files have been cleard out of the later kernels, simply commenting them out of the includes in svgalib_helper/main.c allows it to compile. and it seems to be running my program without a hitch.

---

