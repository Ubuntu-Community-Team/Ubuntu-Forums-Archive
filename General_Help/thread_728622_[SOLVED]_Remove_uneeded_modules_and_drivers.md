---
title: "[SOLVED] Remove uneeded modules and drivers?"
date: 2008-03-19
forum: General Help
---

### Post by tad1073 on 2008-03-19
How do I go about removing uneeded drivers and modules?

---

### Post by kpkeerthi on 2008-03-19
Since ubuntu uses a general purpose kernel, it is compiled with a vast majority of hardware support possible and hence modules. But ubuntu does not load a module unless your PC has a hardware that has a need for it. So your RAM is not wasted.

If you want to remove modules that don't have any use for your hardware, you should consider compiling kernel from source. There is a how to in [ubuntu wiki]("https://help.ubuntu.com/community/Kernel/Compile").

---

### Post by tad1073 on 2008-03-19
Thanks for the link. The reason I was asking is because I was reading the Arch Linux how to and was thinking of giving it a go. But I wanted to see if i could compile an ubuntu kernel that only has drivers and modules for my hardware. I don't know how much disk space that would free up or processes it would cut.

---

### Post by kpkeerthi on 2008-03-19
When you 'configure' your kernel (part of kernel compilation workflow), you can choose the modules you don't need included in kernel code. The description of each modules tells you the size of each modules. Most modules are about 4 to 6 kbs. So if you cut down 10 modules, you will save, on an average, 50 kb from the resulting kernel image. Not quite a savings in my opinion. 

Remember that these modules, if not needed for your system, will anyway be not loaded in  memory. 

And, linux kernel executable is a monolithic process residing in memory. There will not be any additional processes that you can cut down by compiling it from source. 

[http://linuxgazette.net/issue37/martinez.html](http://linuxgazette.net/issue37/martinez.html)

---

