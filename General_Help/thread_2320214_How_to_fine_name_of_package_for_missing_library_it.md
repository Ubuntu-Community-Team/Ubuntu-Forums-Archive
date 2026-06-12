---
title: "How to fine name of package for missing library items?"
date: 2016-04-11
forum: General Help
---

### Post by legendbb on 2016-04-11
I've used ubuntu for almost 10 years.

It always amazes me google search always find me answer for missing package, when I hit "no such file" error.

For my serious EDA project, where tool doesn't officially support ubuntu.

Tried setting up, hit numerous missing libraries (gcc-multilib, g++-multilib, build-essentials, and ...).

Although at the end, I got set up and running, I don't know if I can rely on it.

Can someone please help me to understand, the philosophy of linux packages depending on each other? Risk of version incompatibility?

More specifically, what is the way to find package to install other than google or posting in forum for help?

As an example, I had "fatal error: sys/cdefs.h: No such file or directory", someone asked similar question before and answer is to install libc6-dev-i386. I worked for me, but where is the solution originally from?

Thanks,

---

### Post by steeldriver on 2016-04-11
I find the **apt-file** utility invaluable for this kind of thing

---

