---
title: "CPU Specific Kernel Compile Question"
date: 2008-04-07
forum: General Help
---

### Post by domoso on 2008-04-07
I have a laptop running a P3. I'm interested in compiling a kernel specific for the CPU to take advantage of every last drop of performance from it. I have compiled a kernel successfully and it "feels" like it has a bit more snappyness. I used the generic .config file and changed only the processor family specific to my computer. However, I noticed the madwifi drivers did not load. I'm assuming this is because it's not part of Ubuntu. I may be wrong but, thats not really my question. My question is: Now that I have an "unsupported" kernel will I need to compile drivers specific for my kernel rather than rely on the packages available through synaptic? I'm thinking the answer is yes? Is there a repository out there that offers "pseudo" supported kernels compiled for specific processors? Is there an alternate method for "patching" the generic kernel with cpu specific support and still be "supported"?

---

### Post by dcstar on 2008-04-08
> **domoso said:**
> I have a laptop running a P3. I'm interested in compiling a kernel specific for the CPU to take advantage of every last drop of performance from it. I have compiled a kernel successfully and it "feels" like it has a bit more snappyness. I used the generic .config file and changed only the processor family specific to my computer. However, I noticed the madwifi drivers did not load. I'm assuming this is because it's not part of Ubuntu. I may be wrong but, thats not really my question. My question is: Now that I have an "unsupported" kernel will I need to compile drivers specific for my kernel rather than rely on the packages available through synaptic? I'm thinking the answer is yes? Is there a repository out there that offers "pseudo" supported kernels compiled for specific processors? Is there an alternate method for "patching" the generic kernel with cpu specific support and still be "supported"?

1: Yes.
2: Not that I know of.
3: Doubtful.

The "generic" kernel should work with a P3, if you were using the "386" kernel then that would certainly perform in an inferior way.

---

### Post by mcduck on 2008-04-08
The generic kernel detects your CPU at boot time, and then uses correct optimizations for it. It's quit unlikely that you would get any noticeable benefits from simply compiling the kernel with optimizations for P3.

---

