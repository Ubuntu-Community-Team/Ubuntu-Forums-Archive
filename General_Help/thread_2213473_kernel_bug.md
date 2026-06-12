---
title: "kernel bug"
date: 2014-03-26
forum: General Help
---

### Post by Pedroski55 on 2014-03-26
I don't know if it is important, just thought I'd mention it:

kernel 3.5.0-47-generic must have a bug of some kind. Since this kernel, I cannot boot Ubuntu properly. I am using kernel 3.5.0-23-generic

I have just done a clean install, formatted the partition. Using the older kernel, Ubuntu boots normally. Using the latest kernel, I get some kind of kernel panic output on boot and the computer freezes. This was the reason I reinstalled. Could have saved my time.

First I thought it might be a hardware issue, but Fedora works normally, and this older kernel works fine.

---

### Post by sammiev on 2014-03-26
Not sure why you did a fresh install when you could have just booted up into a older kernel version on boot by selecting advance options. Then you could of tested one of the previous kernel version. Could of have just a bad update as well gone wrong.

---

### Post by coffeecat on 2014-03-26
With kernel 3.5 it sounds as though you are running Quantal - Ubuntu 12.10. It will be going end-of-life next month so it would be advisable to be thinking about which version to replace it with. And since it is a dead end as far as version upgrades are concerned, a new installation would be needed.

---

### Post by Pedroski55 on 2014-03-26
This is 12.04 (.2 I think) LTS I did try older kernels first, but not so far back. I could limp to a start in recovery mode, bad graphics. When I tried to restart the newest kernel again, ....crash.

I don't think this is a hardware issue. Something else is wrong. The last thing I see is kernel output, mentioning rtlc. Can't find it in any log though, I suppose it crashes before it can wrote to a log.

---

### Post by Pedroski55 on 2014-03-31
This is just for your info, maybe someone can find the bug.
I just updated, a new kernel was installed: 3.5.0-48-generic I can't use it, nor 47
I am using:
pedro@pedro-bedro:~$ uname -a
Linux pedro-bedro 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 athlon i386 GNU/Linux
pedro@pedro-bedro:~$

Attached is a pic of the kernel trace output. It was longer, but it ran off the screen before I could grab the camera.

---

