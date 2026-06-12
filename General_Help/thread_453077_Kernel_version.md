---
title: "Kernel version"
date: 2007-05-24
forum: General Help
---

### Post by cuberoot on 2007-05-24
How can I know the kernel version inside ubuntu 7.04?

Thanks!

---

### Post by TheMono on 2007-05-24
Go to a terminal and type 
uname -r

(Having said that, the version will be 2.6.20)

---

### Post by cuberoot on 2007-05-24
kernel.org doesn't seem to have "2.6.20-15-generic" that uname -r reports. I have to mess around the TCP code a bit and I was wondering if it would be okay to just download any 2.6.20 release from kernel.org? 

Is there a good resource available somewhere for building a running a kernel?

---

### Post by TriggerHappyChewie on 2007-05-24
You can compile a custom kernel from kernel.org, there are guides on the forum.  Just search "how to custom kernel".  the 15-generic on your kernel is just an Ubuntu packaging number, not a vanilla kernel thing.

---

### Post by TheMono on 2007-05-24
Yes, to clarify, your kernel version is 2.6.20, and it is the 15th packaging of that kernel with Ubuntu packages, and it is optimised for generic processors.

To get the source for your exact kernel, you can download it complete with the Ubuntu-specific patches via synaptic - it is a package called something like 'linux-source'

---

