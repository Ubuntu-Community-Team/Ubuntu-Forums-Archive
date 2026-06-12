---
title: "kernel bug"
date: 2014-05-12
forum: General Help
---

### Post by Pedroski55 on 2014-05-12
Hi, I am again just posting this for the info of whomsoever looks at such problems.

I have: pedro@pedro-bedro:~$ uname -a
Linux pedro-bedro 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 athlon i386 GNU/Linux
pedro@pedro-bedro:~$ 


This kernel boots and runs well. Later kernels, I think the latest is 3.5.0-50-generic, have a bug. Up to -49 I had a lot of trouble booting. The kernel -50 booted okay. However, I had the wireless switched off. I switched on the wireless, and bang, down went the computer. I get a kernel panic screen, and it mentions rtlc. I can't post it, because it is not logged. Now Ubuntu will not boot using the -50 kernel. Probably, if I switch off the wireless, it will boot again.

So please, someone, tell those concerned that the rtlc driver is causing a crash. Thanks.

---

