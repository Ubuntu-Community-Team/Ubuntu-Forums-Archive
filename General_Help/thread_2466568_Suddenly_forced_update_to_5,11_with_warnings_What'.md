---
title: "Suddenly forced update to 5,11 with warnings? What's up?"
date: 2021-08-30
forum: General Help
---

### Post by GhX6GZMB on 2021-08-30
I regularly update my system using "sudo apt update" and "sudo apt upgrade". This normally leaves the Kernel alone.
But the latest update today suddenly installed 5.11 (existing kernel was 5.8), with a slew of error messages about "i915".

What's going on here? Is the update server gone berserk? Why am I being forced a Kernel update?

---

### Post by monkeybrain20122 on 2021-08-30
It normally would upgrade the kernel if new one is available. I always get kernel updated that way. Which Ubuntu version  is that? I have been on kernel 5.11 for ages, ubuntu 20.04.

---

### Post by oldfred on 2021-08-30
Only if you install 20.04 or 20.04.1 do you keep the orginal 5.4 kernel.

Otherwise you have the enablement stack. This updates kernel for newer systems support. Not really required if original kernel & drivers worked, but some still like to have latest/greatest.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by GhX6GZMB on 2021-08-30
> **monkeybrain20122 said:**
> It normally would upgrade the kernel if new one is available. I always get kernel updated that way. Which Ubuntu version  is that? I have been on kernel 5.11 for ages, ubuntu 20.04.

I've one machine running 5.4.0 and two running 5.8.0 and when they get upgraded it's like 5.4.0-78 to 5.4.0-81 for example. This is fine.
But this is the first time I've experienced a major version jump (5.8 -> 5.11) during a simple update. Kernel updates normally need other commands.
So what' wrong here?

---

### Post by monkeybrain20122 on 2021-08-30
> **ml9104 said:**
> I've one machine running 5.4.0 and two running 5.8.0 and when they get upgraded it's like 5.4.0-78 to 5.4.0-81 for example. This is fine.
But this is the first time I've experienced a major version jump (5.8 -> 5.11) during a simple update. Kernel updates normally need other commands.
So what' wrong here?

Nope, no other commands are needed. It will be upgraded to 5.11 if you have HWE enabled.

---

### Post by GhX6GZMB on 2021-08-30
> **oldfred said:**
> Only if you install 20.04 or 20.04.1 do you keep the orginal 5.4 kernel.

Otherwise you have the enablement stack. This updates kernel for newer systems support. Not really required if original kernel & drivers worked, but some still like to have latest/greatest.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

@oldfred, thanks for the update and the link. Reading it is total gobbledegook, could be from almost any politician. "Enablement Stack" indeed!

So, with this new "Service", I'm forced to accept kernel updates that throw errors, although I have three perfectly working machines with 5.4 and 5.8.

Am I the only one seeing a problem here?

---

### Post by Dennis N on 2021-08-30
The kernel 5.8 is only supplied if you install using Ubuntu 20.04.2 iso - There is no other way to get that kernel with 20.04.
I think when you install 20.04.2 you are then automatically on the schedule for further kernel upgrades which works like this:
When your system becomes 20.04.3 kernel 5.11 is then installed as an automatic update.
When your system becomes 20.04.4 the kernel of Ubuntu 21.10 (to be determined) will be installed.
When your system becomes 20.04.5 the kernel of Ubuntu 22.04 (to be determined) will be installed.

---

### Post by monkeybrain20122 on 2021-08-30
As for your i915 firmware missing problem, there is an easy fix, update linux-firmware with system 76's [ppa]("https://launchpad.net/~system76-dev/+archive/ubuntu/stable").

After that you can just disable the ppa.

---

### Post by Impavidus on 2021-08-31
> **ml9104 said:**
> I regularly update my system using "sudo apt update" and "sudo apt upgrade". This normally leaves the Kernel alone.
**sudo apt upgrade** installs new kernels whenever the installed kernel metapackage is updated and has always done so. **sudo apt-get upgrade** would leave the kernels alone. That's the same for the minor updates (5.11.0-25 to 5.11.0-31) and major updates (5.8 to 5.11).

> **ml9104 said:**
> So, with this new "Service", I'm forced to accept kernel updates that throw errors, although I have three perfectly working machines with 5.4 and 5.8.

Am I the only one seeing a problem here?
If the system was running the 5.4 kernel and receiving upgrades for it, it's not running the HWE kernel and will continue with the 5.4 kernel. If it was running the 5.8 kernel, it is running the HWE kernel and must upgrade to 5.11, as 5.8 is no longer supported. If you don't want these major kernel upgrades every 6 months, stay off the HWE kernels.

I agree, it may be a problem if HWE kernels are encouraged a bit too much.
> **Dennis N said:**
> The kernel 5.8 is only supplied if you install using Ubuntu 20.04.2 iso - There is no other way to get that kernel with 20.04.
I think when you install 20.04.2 you are then automatically on the schedule for further kernel upgrades which works like this:
It seems (if I'm not mistaken) that from Ubuntu Desktop 20.04 (but not Server or the flavours), you're put on HWE kernels automatically. For other releases that only happens from the .2 point release.

---

### Post by grahammechanical on 2021-08-31
The Ubuntu wiki for LTS Enablement Stack says this:

> The 20.04 LTS HWE Stacks continue to follow Rolling Update Model as  documented at the following location, as has been in use since 16.04 LTS  :  [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)   

The Wiki page for Rolling LTS Enablement Stack says this:

> We first introduced the idea of a HWE Kernel in the Ubuntu 10.04 LTS  release, Lucid Lynx.  The HWE kernel was derived and vetted from a newer  kernel shipping in a subsequent interim release of Ubuntu.  These HWE  kernels were released in the LTS point releases as a means to enable  newer platforms and components which required functionality delivered in  these newer kernels.  Both desktop and server images were seeded with  the HWE kernel by default in the point release images.  In addition to  an updated HWE Kernel, for desktop users, an updated X Stack was also  delivered.  Beginning with Ubuntu 12.04 LTS, Precise Pangolin, it was  agreed that users could remain on a HWE stack (ie HWE Kernel + X Stack)  until the subsequent HWE Kernel from the next LTS was introduced in the  images of the 5th point release of the LTS.  Users were then required to  upgrade to this final HWE Stack in order to remain supported with  security updates and ongoing bug fixes.

And this

> Beginning with the Ubuntu 16.04 LTS release, Xenial Xerus, the Kernel  and Foundations team proposed moving to a slightly different model for  maintaining HWE kernels.  Instead of supporting different HWE Stacks in  parallel until we reach the final 5th point release of an LTS, we would  like to roll users forward incrementally as the newer HWE Stacks are  introduced, ie. instantiate a rolling HWE stack.

The answer to the question: "What is go*ng* here?" is surely, "Normal service."

Regards

---

### Post by mIk3_08 on 2021-08-31
> **ml9104 said:**
> I've one machine running 5.4.0 and two running  5.8.0 and when they get upgraded it's like 5.4.0-78 to 5.4.0-81 for  example. This is fine.
But this is the first time I've experienced a major version jump (5.8  -> 5.11) during a simple update. Kernel updates normally need other  commands.
So what' wrong here?
Actually; I am also new to this community but I also experience this  major version kernel jump upgrade from 4 to 5 and it is my first time at that time and very scary but I'm glad that 
I did it smoothly and it was perfect. From 4.x.x to 5.x.x-generic. so for me, just be calm though nothing is perfect but everything will be alright.  

> **oldfred said:**
> Only if you install 20.04 or 20.04.1 do you keep the orginal 5.4 kernel.
Otherwise you have the enablement stack. This updates kernel for newer systems support. Not really required if original kernel & drivers worked, but some still like to have latest/greatest.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Thanks for this linked oldfred it help me a lot. I just did a tracing on all of my terminal commands and I just saw the same command you shared on the linked and I did installed exactly 
the perfect kernel on my Linux Ubuntu Operating System.

---

### Post by GhX6GZMB on 2021-08-31
OK, so it's back to a reinstall with 20.04.1 (5.4.0 kernel). Damn! I hate messing with a perfectly running system, but I'm apparently being forced to do so. I cannot accept a kernel upgrade throwing warnings and errors. I feel set back to my M$ days where I didn't have a choice in any matter.

---

### Post by monkeybrain20122 on 2021-08-31
> **ml9104 said:**
> OK, so it's back to a reinstall with 20.04.1 (5.4.0 kernel). Damn! I hate messing with a perfectly running system, but I'm apparently being forced to do so. I cannot accept a kernel upgrade throwing warnings and errors. I feel set back to my M$ days where I didn't have a choice in any matter.

Really not sure what your problem is. It works great across my several machines. The i915 firmware missing warning can be fixed easily by upgrading linux-firmware as I said in my last post.

BTW, aren't you using timeshift? so you shouldn't need to reinstall. In any case if you don't want the new kernel it is quite simple, boot into the old one and then delete the new one and disable hwe so not even timeshift is needed.

---

### Post by GhX6GZMB on 2021-08-31
@[[COLOR=#000000]monkeybrain20122[/COLOR]]("https://ubuntuforums.org/member.php?u=1843403")      
I was not aware of this option, Thank You!

I've now followed this recipe: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I*m happy again. :)

On EDIT: Not really happy. uname - a still reports 5.11 I'm investigating...

OK, fixed. I'd missed the final command in the recipe. Kernel is now 5.4.0-81. But the apt remove --purge command gives some really heavy warnings. Someone without a Timeshift backup would run away screaming...

---

