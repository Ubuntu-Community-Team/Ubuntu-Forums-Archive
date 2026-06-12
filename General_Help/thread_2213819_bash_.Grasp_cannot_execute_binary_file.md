---
title: "bash ./Grasp cannot execute binary file"
date: 2014-03-28
forum: General Help
---

### Post by jing_liu on 2014-03-28
Hey, i am new to unix system. I had ubuntu 13.10 32bit installed on my pc. 
when i tried to run program Grasp, it shown bash ./Grasp cannot execute binary file. 
I checked the file as a previous post with typing file Grasp, 
it shown Grasp: ELF 32-bit MSB executable, MIPS, MIPS-I version 1 (SYSV), dynamically linked (used shared libs), not striped
can anyone help me to solve the problem or tell me what could be the possible reason? Thanks

---

### Post by mcduck on 2014-03-28
It seems you have a [MIPS]("http://en.wikipedia.org/wiki/MIPS_architecture") binary file instead of x86 one. It's intended for a completely different processor architecture, and I doubt you'd be able to run it on a PC.

Where did you get the file from? Try to look again if they'd have a x86 binary available.

---

### Post by jing_liu on 2014-03-28
yes, you are right. I went back to their website, in the description it said it is for SGI machines only. I will use their windows version. Thank you very much for your reply!

---

