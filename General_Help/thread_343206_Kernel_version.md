---
title: "Kernel version"
date: 2007-01-21
forum: General Help
---

### Post by Doug11 on 2007-01-21
OK, I was doing some reading trying to figure out a couple probs I'm having and come across something interesting. From what I can tell, you kernel headers should be one of 4 flavors,,IE. ,,<386, 686, k7, or server>

But when I run the following comand I get something a little different.

doug@home:~$ uname -r
2.6.19.1

I'm quite sure that when I upgraded kernel version I chose k7. I'm running Edgy64 on AMD64 machine. Does this look right? Or what should I do to fix this?

---

### Post by pay on 2007-01-21
Edgy doesn't use the 2.6.19.1 kernel. You or someone else using your computer must of compiled the kernel manually.

---

### Post by Doug11 on 2007-01-21
I actually compiled the kernel from this thread 

[http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158)

---

### Post by pay on 2007-01-21
whither you did ```
make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
```or```
make-kpkg -initrd --revision=686 kernel_image kernel_headers modules_image
```etc would determine your kernel headers. The name the kernel has doesn't really matter.

---

