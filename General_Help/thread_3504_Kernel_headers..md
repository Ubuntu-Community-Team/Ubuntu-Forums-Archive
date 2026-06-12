---
title: "Kernel headers."
date: 2004-11-06
forum: General Help
---

### Post by tvlad on 2004-11-06
I know it may seem a bit strange, but what exactly are kernel headers, i mean i'm looking for a short definition, i want to know what are they good for.

---

### Post by im_ka on 2004-11-06
[http://linux.about.com/cs/linux101/g/Kernel_headers.htm](http://linux.about.com/cs/linux101/g/Kernel_headers.htm)

---

### Post by az on 2004-11-06
When you compile software from source, you are creating the binary files and you also have header files which define the functions of the binary (object) files you just made.  
To reuse the functions in the object files you can compile another program using the already compiled object files.  You tell it what the functions are by using the headers.

If you are not going to compile anything, you only need the binaries.

If you want to add modules (drivers) to your kernel, most of their source sode can be used with different kernels.  All you need is either the kernel source with the exact configuration of your own kernel or your kernel's headers...

---

