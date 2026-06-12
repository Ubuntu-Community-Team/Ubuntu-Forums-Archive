---
title: "&quot;optimize for size&quot;"
date: 2005-10-16
forum: General Help
---

### Post by eraclito on 2005-10-16
I tryed  to compile 2.6.12 kernel source whin the new feature "optimize for size"
so i made a very light vmlinuz (less then 1 mb) but after reboot it stops at 
uncompressing and booting the kernel

someone made it works?

eraclito

---

### Post by eraclito on 2005-10-17
[QUOTE=eraclito]I tryed  to compile 2.6.12 kernel source whin the new feature "optimize for size"
so i made a very light vmlinuz (less then 1 mb) but after reboot it stops at 
uncompressing and booting the kernel

someone made it works?

eraclito[/QUOTE]

any idea?

---

### Post by afonic on 2005-10-17
If you haven't removed the old kernel (the default ubuntu one) just boot with that.

---

### Post by eraclito on 2005-10-17
[QUOTE=afonic]If you haven't removed the old kernel (the default ubuntu one) just boot with that.[/QUOTE]

yes i did that, and i recompile the source whitout  "optimize for size", but i'd like to know if someone can use that option and if it can improve system prerformance...

---

### Post by GoA on 2005-10-17
Yes, I used it and kernel is working fine. Did you remember to change the GCC to 3.4 from 4 version? Did you also compile file systems as modules? And to be honest I didn't find any speed difference even I removed a lot of stuff from the kernel.

---

### Post by eraclito on 2005-10-17
[QUOTE=GoA]Yes, I used it and kernel is working fine. Did you remember to change the GCC to 3.4 from 4 version? Did you also compile file systems as modules? And to be honest I didn't find any speed difference even I removed a lot of stuff from the kernel.[/QUOTE]

I have installed gcc 3.4 and 4 both and i compile all file systems as modules.

but if it not make any improvement no big deal I'll stay like i'm (my system, after add preempting, goes quite fast)

by

eraclito

---

### Post by GeirG on 2005-10-17
Hi,

I am no expert on kernel compiling, but general programmer knowledge suggests (at least to me) that optimizing for size does just that, optimizes for the size of the kernel image, and more likely reduces performance than otherwise.
In a very simplified way I would say you optimize for either size **or** speed.
They are probably not totally mutually exclusive, but as a rule of thumb I think it is kinda correct.

Regards

---

### Post by afonic on 2005-10-17
Well in the kernel subject, Ubuntu contains only i386 so most users stick to that.

They should really install the version best of their machine (686 for Pentium4, k7 for Athlon) as the whole system runs much faster that the default 386 one. It can be simply done via Synaptic and its trouble free even for the less experienced ones, as if something goes wrong, you can still boot the old kernel.

---

