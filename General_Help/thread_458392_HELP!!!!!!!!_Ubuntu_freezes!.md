---
title: "HELP!!!!!!!! Ubuntu freezes!"
date: 2007-05-29
forum: General Help
---

### Post by juantovarm on 2007-05-29
Hello all! I ahve a very big problem, all my ubuntu installations freeze, even the live cd (burnt at 4x and checked for erros, as well as the shipit cd's) the moment X starts. No problem with the command line. I tried fedora core 6 and had the same result. Only with debian and zenwalk does the pc run properly, but i have gotten used to ubuntu for many reasons and i would like to have a working ubuntu box

System specs:
mb: gigabyte technologies K8 triton series K8NS Pro
video card: GV-N40 Series GV-N40128TE/GV-N4064T Powered by Nvidia GeForce MX4000 Graphic Pzrocessing Unit
AMD64
512 Ram
80 gigas HD
:confused:

---

### Post by energiya on 2007-05-29
Do you have any error output in the systemlog?

If it runs on Zenwalk and Debian, but not on Ubuntu and FC6, it might be a kernel issue. Try compiling the kernel in Ubuntu using the .config file from Zen or just install the Debian kernel (I think it should work).

If it isn't the kernel... well... it could be a lot of things, and I don't see how you could "debug" this...

---

### Post by juantovarm on 2007-05-30
I am very sorry, but could you tell me how to compile the kernel? I haven't done any fancy stuff like that

---

### Post by energiya on 2007-05-30
Just search the forum... there are a lot of threads describing how to do this.

---

