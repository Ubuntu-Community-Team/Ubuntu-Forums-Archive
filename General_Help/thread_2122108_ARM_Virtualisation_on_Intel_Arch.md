---
title: "ARM Virtualisation on Intel Arch"
date: 2013-03-04
forum: General Help
---

### Post by ATAQ on 2013-03-04
Hey all, I'm looking for some sort of virtualisation software that will run my compiled ARM build distros on Intel machines, for testing purposes.

Any help would be great,
Thanks,
Anthony

---

### Post by 3rdalbum on 2013-03-04
> **ATAQ said:**
> Hey all, I'm looking for some sort of virtualisation software that will run my compiled ARM build distros on Intel machines, for testing purposes.

Semantics here:

"Virtualisation" can only be done where the CPU architecture is the same. Virtualisation is where the CPU runs the guest OS code, with it only going through a very thin layer of translation; nothing more than that thin layer is needed, because the underlying CPU can understand the guest OS' code. This is quite fast as almost nothing needs to be done to the code. However, no Intel x86 CPU can understand ARM instructions, full stop, so virtualisation will not help you.

What you want is emulation - where a piece of software converts ARM instructions to x86 instructions on-the-fly. This is a lot slower than virtualisation as the software has to do a lot more work; the real CPU is spending a lot of its power doing the conversion process before it can actually run the line of code.

Qemu can emulate some ARM systems, but you probably need to know exactly what ARM system you want to emulate. Code compiled for one ARM SoC won't run on another one.

---

