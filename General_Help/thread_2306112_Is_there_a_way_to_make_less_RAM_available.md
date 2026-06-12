---
title: "Is there a way to make less RAM available?"
date: 2015-12-12
forum: General Help
---

### Post by vasa1 on 2015-12-12
There's this thread: [No performance improvement after adding Ram]("http://ubuntuforums.org/showthread.php?t=2306090")
I seem to remember reading about a way to make *less* RAM available to the system. Is that possible? If it's possible, a user with 2 GB RAM could reduce the RAM available just a bit and see if things got *worse*. Then wouldn't that be a hint that increasing RAM may be beneficial (for the intended usage)?

---

### Post by TheFu on 2015-12-12
Pull a stick out?

---

### Post by sudodus on 2015-12-12
You can use the boot option mem

for example **mem=384M**

```
mem=nn[KMG]	[KNL,BOOT] Force usage of a specific amount of memory
			Amount of memory to be used when the kernel is not able
			to see the whole system memory or for test.
			[X86] Work as limiting max address. Use together
			with memmap= to avoid physical address space collisions.
			Without memmap= PCI devices could be placed at addresses
			belonging to unused RAM.
```

from [Documentation/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/kernel-parameters.txt)

I have used this boot option to test how much RAM is necessary for ubiquity and the one button installer to work.

---

