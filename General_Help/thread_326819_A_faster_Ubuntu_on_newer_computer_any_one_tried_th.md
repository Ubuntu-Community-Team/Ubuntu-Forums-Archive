---
title: "A faster Ubuntu on newer computer?? any one tried this"
date: 2006-12-28
forum: General Help
---

### Post by zazen666 on 2006-12-28
Hello all,
I found this information. has anyone tried it? I would like to give it a shot and see but I would like to hear feedback to see if it has any prolems or if it really works...


[http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50](http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50)

10. A new kernel 

Ubuntu will install a 386 kernel for x86 machines,
which probably isn't what you'd want if you've got a
Pentium II or better CPU. The 386 kernel is compiled
to work with just about any x86 CPU, but extensions
that appear in later CPUs can give your system a
boost, if they're taken advantage of. To replace the
kernel, open Synaptic or Adept and search for
linux-image. You'll see several choices. Pick the one
that best suits your CPU -- probably the
linux-image-686 package for Pentium II and later CPUs,
and linux-image-k7 for later AMD processors. Note that
if you're using the AMD64 line (or Intel's x86-64
CPUs) you should be using the amd64 images.

Of course, once you install the new kernel, you'll
need to reboot. Another benefit to the 686 kernels is
that they have SMP support, which is a bonus for
multi-core and Intel HyperThread CPUs.

---

### Post by Olav on 2006-12-28
> **zazen666 said:**
> Hello all,
I found this information. has anyone tried it? I would like to give it a shot and see but I would like to hear feedback to see if it has any prolems or if it really works...


[http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50](http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50)

10. A new kernel 

Ubuntu will install a 386 kernel for x86 machines,
which probably isn't what you'd want if you've got a
Pentium II or better CPU. The 386 kernel is compiled
to work with just about any x86 CPU, but extensions
that appear in later CPUs can give your system a
boost, if they're taken advantage of. To replace the
kernel, open Synaptic or Adept and search for
linux-image. You'll see several choices. Pick the one
that best suits your CPU -- probably the
linux-image-686 package for Pentium II and later CPUs,
and linux-image-k7 for later AMD processors. Note that
if you're using the AMD64 line (or Intel's x86-64
CPUs) you should be using the amd64 images.

Of course, once you install the new kernel, you'll
need to reboot. Another benefit to the 686 kernels is
that they have SMP support, which is a bonus for
multi-core and Intel HyperThread CPUs.

This information is outdated for Ubuntu 6.10 (Edgy) which uses a generic kernel for all the Pentium/AMD processors. I believe this generic kernel "adapts itself" to whatever processor it finds in your computer. Rather neat, actually.

---

### Post by Death4Life on 2006-12-28
just one question: how do i know to what it adapted.

And one more: can a core 2 duo run the x86-64 version as well since everytime i see x64 there always is amd64 ( rather confusing )

---

### Post by TheWizzard on 2006-12-28
> **zazen666 said:**
> Hello all,
I found this information. has anyone tried it? I would like to give it a shot and see but I would like to hear feedback to see if it has any prolems or if it really works...


[http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50](http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50)

10. A new kernel 

Ubuntu will install a 386 kernel for x86 machines,
which probably isn't what you'd want if you've got a
Pentium II or better CPU. The 386 kernel is compiled
to work with just about any x86 CPU, but extensions
that appear in later CPUs can give your system a
boost, if they're taken advantage of. To replace the
kernel, open Synaptic or Adept and search for
linux-image. You'll see several choices. Pick the one
that best suits your CPU -- probably the
linux-image-686 package for Pentium II and later CPUs,
and linux-image-k7 for later AMD processors. Note that
if you're using the AMD64 line (or Intel's x86-64
CPUs) you should be using the amd64 images.

Of course, once you install the new kernel, you'll
need to reboot. Another benefit to the 686 kernels is
that they have SMP support, which is a bonus for
multi-core and Intel HyperThread CPUs.


works great except for amd64, because you run into troubles with 32 bit windows codecs.

---

### Post by maxamillion on 2006-12-28
yes, an intel core2 duo will run the x86-64 bit kernel just fine. the main reason the installation image is called amd64 is because at its time of creation, it was the only 64-bit desktop processor on the market. Both the intel core2 duo and amd64 processors are x86-64 compliant and will both run the same code, you will be fine. The thing about 32-bit windows codecs is a problem that would be found on any 64-bit machine and not just the intel processor.

---

