---
title: "compile source code on 32bit and 64bit system?"
date: 2023-06-11
forum: General Help
---

### Post by ubto66 on 2023-06-11
if you have the source code for a program, can you compile it
on both a 32bit and 64bit computer? Thank you.

---

### Post by grahammechanical on 2023-06-11
I do not know the answer to your question. I do know that a 32 bit Linux OS will run on a 64 bit CPU. The 64 bit CPUs designed by Intel and AMD are backwards compatible with 32 bit CPUs. This is because when those companies released 64 bit CPUs there were not any 64 bit operating systems to run on them. So for years those who brought the latest hardware (64 bit CPU) with an OS pre-installed (Windows) got a 32 bit OS running on a 64 bit CPU.

By now you should have worked out that 64 bit operating systems and programs/applications can not run on 32 bit CPUs.

Imaging that the actual compiling of the code can be done on either a 32 bit or 64 bit CPU. I  have no practical experience of that.

Regards

---

### Post by Holger_Gehrke on 2023-06-11
Depends on the program. An example: the Odyssey2 emulator o2em was written for 32 bit systems. It uses variables of type 'int' and assumes that those are 32 bit. It will compile on a 64 bit system but segfault almost immediately.

Holger

---

### Post by Impavidus on 2023-06-11
With most, in particular simpler, programs, it just works. You can compile the source code for 32 bit or 64 bit and both programs will function the same. There will be a difference in memory use and if you're not careful, the 32 bit version and the 64 bit version may be unable to talk to each other, even when 32 bit versions can talk to other 32 bit versions and 64 bit versions to 64 bit versions. But there are cases where it doesn't work, where the wrong version gives unexpected results, segfaults or fails to compile.

---

