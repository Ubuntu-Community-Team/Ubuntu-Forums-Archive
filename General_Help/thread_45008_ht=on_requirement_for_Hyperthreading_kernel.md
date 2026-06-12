---
title: "ht=on requirement for Hyperthreading kernel"
date: 2005-06-28
forum: General Help
---

### Post by emmet on 2005-06-28
Hello all,

This may be a silly question, but I hope someone can clear it up for me.

On the 23rd May, a patched kernel was released in order to correct some security issues in the 2.6 kernel. This changed the version number to 2.6.10-34.1 (for the 2.6.10 kernel).

At that time, it was recommended that a kernel parameter ht=on was passed if you were willing to take the risk of the CAN-2005-0109 exploit (which was concerned with threads in a hyperthreading cpu. I took the choice to enable hyperthreading on my machine and so added the kernel parameter.

Since then, another patched kernel has been released, and I've installed that (now my version number is 2.6.10-34.2). 

Having a look in /boot/grub/menu.lst, I see that the ht=on parameter has been removed. 

Does anyone know if hyperthreading has been reenabled by default for smp kernels or should I edit the menu.lst file again to add the ht=on parameter?

As I mentioned, this may be a silly question, but I am very cautious when messing about with my boot files.

Current entry is:

```
 /boot/vmlinuz-2.6.10-5-686-smp root=/dev/hda1 ro quiet splash
``` 

If the ht=on parameter has to be entered again, then I assume it should now read:

```
 /boot/vmlinuz-2.6.10-5-686-smp root=/dev/hda1 ro quiet splash ht=on
``` 

Thanks in advance,

Emmet

---

### Post by shakin on 2005-06-28
Unless I've been doing something wrong, all I've ever done is run the SMP kernel to use hyperthreading. No boot paramaters necessary.
```

$ grep processor /proc/cpuinfo

```
Should show two processors if ht is enabled. It'll show up like this:
```

processor       : 0
processor       : 1

```

---

