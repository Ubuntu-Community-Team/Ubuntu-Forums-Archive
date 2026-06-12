---
title: "How often should I update the Kernel?"
date: 2008-07-06
forum: General Help
---

### Post by Tribulation on 2008-07-06
I've been wondering for awhile, how often should I update my kernel? I still have 2.6.24.

---

### Post by sdennie on 2008-07-06
I believe Hardy will always run 2.6.24.  The updates you see in update-manager will mostly be security related so, I would recommend updating whenever you see a kernel update.  Regardless of what the update manager says, it's not actually necessary to immediately reboot but, you won't actually see the updates until you reboot.

---

### Post by brian_p on 2008-07-06
> **Tribulation said:**
> I've been wondering for awhile, how often should I update my kernel? I still have 2.6.24.

Do it and you lose the benefit of automatic security updates. But if you have hardware which will only work with a newer kernel it is your only option.

---

### Post by Tribulation on 2008-07-06
Well I'll just stick with what I have then. Why does updating the kernel disable automatic security updates?

---

### Post by shae on 2008-07-06
What he is referring to is if you compile your own kernel, then it is up to you to provide security updates to your kernel.  Generally tracing the latest version from kernel.org is safe, but it bugs and security flaws are possible.  If you continue to use the Ubuntu stock kernel, the Ubuntu team updates it with security patches when needed.

---

### Post by Frak on 2008-07-06
There can be issues with building and installing your own kernel. So for normal use, its just recommended to let the Packaging Team provide security tested and stable kernel for you.

Though...

If you still want to compile and install your own kernel, you may want to check out [KernelCheck]("http://kcheck.sourceforge.net/"), which does this for you with a nice graphical interface (and a 3-4 hour wait time + 5-10GB of space needed to build, this is normal)

---

