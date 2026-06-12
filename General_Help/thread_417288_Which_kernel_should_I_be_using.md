---
title: "Which kernel should I be using?"
date: 2007-04-21
forum: General Help
---

### Post by NickPresta on 2007-04-21
I have the AMD Athlon 64 X2 4200+ processor and I'm running the generic kernel on Kubuntu (i386 desktop version).

*uname -a* returns: Linux username 2.6.17-11-generic #2 SMP Tue Mar 13 23:32:38 UTC 2007 i686 GNU/Linux


What are the benefits of running another kernel over the "generic" kernel?

Thank you.

---

### Post by skip27 on 2007-04-21
Sounds like you're running Edgy /w the latest updates, is that correct?

For the most part, using the generic kernel is fine, as it contains very broad hardware support and is supposed to serve as the lowest common denominator for all machines. There are only a few reasons why you'd want to recompile your kernel:

[LIST=1]
[*]You need certain functionality that isn't available in the generic kernel.
[*]The generic kernel is acting quirky with your setup.
[*]You're curious.
[*]You want to recompile the kernel with optimizations.
[*]Some other reason, but implies that you know what you're doing.
[/LIST]

I had to recompile the kernel after upgrading to Feisty, since it was acting quirky. For some odd reason, my external USB HD would automount at startup, but Linux didn't think it was mounted. So, basically, I had FULL access to the drive through my /media directory, yet I couldn't unmount it, since it didn't register as a mounted drive to begin with. After recompiling the kernel, which took about half an hour /w all the modules, everything is just peachy. Besides, I got the opportunity to tweak a few options and compile with optimizations. Just in case you're curious, I'm using a vanilla kernel ([www.kernel.org](www.kernel.org)), version 2.6.20.7. I used the '-O2 -march=athlon-xp -fomit-frame-pointer -pipe' optimizations. Of course, you have to be careful with optimizations. But that's the subject for another thread.

---

### Post by NickPresta on 2007-04-21
I have Edgy with all updates and my hardware support it perfect, as far as I know.
I am in the middle of upgrading to FF.


I don't really want to fix what isn't broken, so to speak, I was just curious whether or not there was any inherent benefit in using another kernel.


Thanks for the information.

---

