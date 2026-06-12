---
title: "Is any way to copy/backup a custom kernel"
date: 2019-03-20
forum: General Help
---

### Post by zaknafein99 on 2019-03-20
Hello,

I work in a highschool with 15 ubuntu  classrom computers, they have a custom kernel that as far as I know have the drivers for the sound card/chip, with the vanilla kernel sound is unavailable. Is there a way to backup/copy said kernel to install it to another computer wich does not boot due to a kernel problem?

Thanks

---

### Post by TheFu on 2019-03-20
Copy the file?  Is this a trick question?

---

### Post by zaknafein99 on 2019-03-20
Ha! I wish it is a trick question. 

Where are those files located?

---

### Post by TheFu on 2019-03-20
> **zaknafein99 said:**
> Ha! I wish it is a trick question. 

Where are those files located?

/boot/

But there are almost certainly other dependencies tied to the kernel, but that is where they are stored normally.  Since the 1990s, Linux kernels have used a module addon method to support most hardware.  Things like sound cards are always supported through a module - like 99.9999% of the time.  All the other kernel modules need access to the kernel source code.  You can see the loaded modules using **lsmod**.

With a custom kernel, you'd need to check the boot management tool to determine where any specific kernel is located. With a custom setup, they can be almost anywhere.

There is also the problem of using old kernels full of exploits, especially in a school environment.  Local escalations can happen. There are many available: [https://github.com/xairy/linux-kernel-exploitation](https://github.com/xairy/linux-kernel-exploitation)

I have doubts that backing up the 1 kernel file will let you restore just that file to some other system and have things "just work."  [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) explains the way to build a kernel on Ubuntu. This will show some of the dependencies.

---

### Post by zaknafein99 on 2019-03-20
Ok. Thank you very much for the answer, I'll se what I can do

---

