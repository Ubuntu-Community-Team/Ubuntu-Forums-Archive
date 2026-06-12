---
title: "nvidia kills me !!!"
date: 2007-01-27
forum: General Help
---

### Post by energiya on 2007-01-27
Hi,
I have just recompiled 2.6.19-2 kernel with the Suspend2 patch hoping to hibernate. Also installed hibernate script. This is what I get when running it:
> 
Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).


dmesg | grep Suspend2 spits out this:
> 
Suspend2 Userspace Storage Manager support registered.
Suspend2 Userspace UI support registered.
Suspend2 Compressor support registered.
Suspend2 Encryptor support registered.
Suspend2 Block I/O support registered.
Suspend2 Swap Allocator support registered.
Suspend2 File Allocator support registered.
Suspend2: SwapAllocator: Signature found.
Suspend2: Resuming enabled.
Suspend2: Normal swapspace found.


Suspend to RAM worked before patching the kernel with Suspend2 and works now.
What must I do to get hibernate working?!?:( :(

---

### Post by energiya on 2007-01-27
ooookkk.... recompiled kernel and disabled agpgart, and now hibernate and resume work... only when I kill X... and suspend 2 ram is dead :(:(

---

