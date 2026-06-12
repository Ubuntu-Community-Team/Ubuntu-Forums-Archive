---
title: "511MB Kernel!"
date: 2007-03-11
forum: General Help
---

### Post by nfm on 2007-03-11
Hello all,

I have compiled kernel 2.6.20.2 that resulted in 506MB of size. I have replaced all occurrences of 'O2' in makefile with 'O4' (OX are the levels of optimizations performed by gcc compiler), I hoped to see speed improvement but did not expect such a big size. The config that was used was the default one from Fiesty Fawn Herd 5 with few CPU tweaks. I don't see any slowdowns so my question is if this is OK or should I recompile?

---

### Post by yabbadabbadont on 2007-03-11
Well, as long as you don't mind 506MB of your system's memory always being used by the loaded kernel and you have plenty more to spare, then maybe...  but grub will probably refuse to load that monster.  Besides, anything over -O3 (and sometimes that) usually results in breakage in the program that is compiled with it.

---

### Post by nfm on 2007-03-11
Interesting yabbadabbadont,

Both the monster and standard kernel boot in 55 seconds from grub into the desktop. Compressed linux-image-2.6.20.2_K8_i386.deb resulted in 203MB  (~506MB uncompressed). initrd.img-2.6.20.2 is 39.9MB and initrd.img-2.6.20-9-generic is 6.5MB. Most of the size came from /lib/modules/2.6.20.2/kernel/drivers, 311MB. I will most certainly never do such a thing again :mrgreen:

---

### Post by yabbadabbadont on 2007-03-11
Oh, I thought you were talking about the actual kernel, not the initrd image...  What is the size of the actual kernel?  (the resident portion without modules) It is what is specified in menu.lst by the kernel line.

---

### Post by nfm on 2007-03-11
If I understand correctly, you mean vmlinuz? If yes, it is 1.7MB compared to vmlinuz-2.6.20-9-generic that is 1.5MB. I'm starting to wonder if there's a performance gain, I'll google what tests I might do. I know from my own experience that x264 (H.264 Encoder) gave me 8% boost in overall encoding speed compared to 'O2'.

---

### Post by 3rdalbum on 2007-03-11
```
sudo modprobe -r kitchen-sink
``` :-P

---

