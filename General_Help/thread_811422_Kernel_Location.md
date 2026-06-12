---
title: "Kernel Location"
date: 2008-05-29
forum: General Help
---

### Post by angry_jew on 2008-05-29
I'm reading the book Understanding the Linux Kernel by OReilly and I'm having a difficult time locating the function calls that it references.  Where is the Linux kernel located?  I thought it was /boot/initrd.img-2.6.22-14-generic but whenever I open it with a text editor it shows a bunch of symbols and characters I don't understand.

How can I view the function calls and data structures?

---

### Post by ad_267 on 2008-05-29
That's the compiled kernel. If you want to have a look at the source code you need to download it.

This might be of some use: [https://help.ubuntu.com/community/Kernel/](https://help.ubuntu.com/community/Kernel/), [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) and [https://wiki.ubuntu.com/KernelGitGuide](https://wiki.ubuntu.com/KernelGitGuide)

This thread is old but might be useful: [http://ubuntuforums.org/showthread.php?t=200634](http://ubuntuforums.org/showthread.php?t=200634)
I'm sure there must be a lot of info out there on this topic if you know where to look.

---

### Post by Thanoulis on 2008-05-29
You can also download it from [here]("http://www.kernel.org/").

---

### Post by MaindotC on 2008-05-29
You know I've always wondered this as well - I'm looking in the directory specified by the wiki and I don't see anything that I can open w/ a text editor and contains C code with function calls.

---

### Post by inportb on 2008-05-29
**/boot/initrd.img-2.6.22-14-generic** is *not* the kernel. As its name implies, it's the ramdisk image that bootstraps the rest of the system ;p

---

### Post by MaindotC on 2008-05-29
Still not finding any .c files...

---

### Post by WRDN on 2008-05-29
As others have pointed out, to view the kernel source you will have to download it.
Also, you can view the compiled kernels at: /usr/src

---

