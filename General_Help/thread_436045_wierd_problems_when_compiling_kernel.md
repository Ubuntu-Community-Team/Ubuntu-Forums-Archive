---
title: "wierd problems when compiling kernel"
date: 2007-05-07
forum: General Help
---

### Post by agentstewie on 2007-05-07
i am trynig to compile my own kernel for speed improvements, but for some reason, the intel wireless 3945abg doesnt work any more.. It works with the standard kernel, (feisty kernel) but not with the one i compile.
any ideas?
also, can you add any SSE2/SSE3/SSSE3 optimaztions for the kernel for speed improvements?

---

### Post by agentstewie on 2007-05-07
bump?

---

### Post by jjmatt on 2007-05-08
When you compiled the kernel did you A) use the ubuntu kernel? i.e.

```
sudo apt-get install linux-source
```

B) compile your kernel off the working config file? i.e.

```
sudo cp /boot/config-`uname -r`/usr/src/linux-source-[number] 
sudo make menuconfig
```

---

### Post by agentstewie on 2007-05-08
hmm does it really matter, if i try compiling the ubuntu kernel or the standard vanillla kernel?

---

### Post by jjmatt on 2007-05-08
Well I'm not sure that it actually "matters" but it makes errors like this more easily avoid able. I tried the same thing a while back and I couldn't even get it to boot. The stock ubuntu kernel comes with patches that most people use, namely the intel wireless drivers. Also, if you work off your working config file you KNOW everything that was working before will continue to work because nothing was disabled (except possibly things you knew you didn't need. you didn't forget to enable things you needed). 

If you must use a vanilla kernel make sure your specific wireless card is enabled in the kernel and any patches are added to the kernel.

---

