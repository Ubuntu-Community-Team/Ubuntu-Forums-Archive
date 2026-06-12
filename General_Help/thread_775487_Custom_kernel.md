---
title: "Custom kernel"
date: 2008-04-30
forum: General Help
---

### Post by defmomo on 2008-04-30
I downloaded the current kernel, and am thinking of compiling and installing it my ubuntu install, after stripping it of all the components I don't need, like support for some filesystems, or hardware, and maybe choose some compile-time optimizations. I'm using  the xconfig right now, and it all seems straightforward. I just have a few questions: Will it overwrite my current kernel if I "make install"? How do I add it as a boot-time option in grub? (I've seen some config files, and the kernel is specified) Finally, how big of an advantage will slimming thow the kernel bring?

---

### Post by renzokuken on 2008-04-30
first off, awesome avatar dude !!! :-P

it shouldnt overwrite your current kernel no. it should create an extra kernal alongside which can be added to grub so you can choose to boot from the original kernel (good failsafe in case your one doesnt work) or you're own custom kernel

read here first [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by rubicon on 2008-04-30
Among renzokuken's post, I'd say that the *speed-wise* advantages of self-compiled kernel is not so significant (in fact, almost not significant at all) *for P4 and later*. I you use Core 2 Duo, for example, it won't bring the real boost, it just may slightly speed up boot process and cputime-consuming calculations.

---

### Post by defmomo on 2008-04-30
> **renzokuken said:**
> first off, awesome avatar dude !!! :-P
Thx! Strangely, I find yours nice too! :KS

Reading the link you gave me, and I will definitely try out several kernel combinations.(=> Will enjoy it too!)
[QUOTE=rubicon]
 Among renzokuken's post, I'd say that the speed-wise advantages of self-compiled kernel is not so significant (in fact, almost not significant at all) for P4 and later. I you use Core 2 Duo, for example, it won't bring the real boost, it just may slightly speed up boot process and cputime-consuming calculations.
[/QUOTE]
I'm mostly doing this to learn about kernels and Linux (thinking bout getting a linux-powered server to work on a PlayStation 2 :lolflag:), but it's also pretty cool, and I get to geek out doing it. Speed gains, no matter how little, would be a welcome side effects.

---

### Post by renzokuken on 2008-04-30
it is an excellent way to learn indeed. just make sure you are prepared for problems (i.e. failsafe kernel). not that you should have any but just in case...... >_<

---

### Post by rubicon on 2008-04-30
> **defmomo said:**
> Thx! Strangely, I find yours nice too! :KS

Reading the link you gave me, and I will definitely try out several kernel combinations.(=> Will enjoy it too!)

I'm mostly doing this to learn about kernels and Linux (thinking bout getting a linux-powered server to work on a PlayStation 2 :lolflag:), but it's also pretty cool, and I get to geek out doing it. Speed gains, no matter how little, would be a welcome side effects.
Good luck then :KS

BTW, have you read this: [https://wiki.ubuntu.com/MeetingLogs/openweekhardy/UpstreamKernels](https://wiki.ubuntu.com/MeetingLogs/openweekhardy/UpstreamKernels) ?

---

