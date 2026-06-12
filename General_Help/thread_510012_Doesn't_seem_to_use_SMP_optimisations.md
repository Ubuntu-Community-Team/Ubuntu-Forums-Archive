---
title: "Doesn't seem to use SMP optimisations"
date: 2007-07-26
forum: General Help
---

### Post by Eddy Dean on 2007-07-26
Hello,

I recently got an new, 64Bit Dual Core AMD processor (AMD Athlon 64 X2 5600+). After installing the 64-bit version of Ubuntu on it I noticed something strange. No matter what I do, the CPU usage doesn't get above 50%, even when doing things like video converting etc. Is this because the kernel is not optimized for dual-core, or because the conversion is likely to be single-threaded.

When running cpuburn twice (!) both cores reach 100%. What is the point of dual core when Ubuntu doesn't use both cores after all? Why does it have to be a generic kernel, instead of one specialized for your CPU?

Here's my uname -a:
Linux links 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

I haven't seen any guides for a custom kernel in Feisty, and there doesn't seem to be an 64-bit dual core kernel in apt.

---

### Post by mcduck on 2007-07-26
> **Eddy Dean said:**
> Hello,

I recently got an new, 64Bit Dual Core AMD processor (AMD Athlon 64 X2 5600+). After installing the 64-bit version of Ubuntu on it I noticed something strange. No matter what I do, the CPU usage doesn't get above 50%, even when doing things like video converting etc. Is this because the kernel is not optimized for dual-core, or because the conversion is likely to be single-threaded.

When running cpuburn twice (!) both cores reach 100%. What is the point of dual core when Ubuntu doesn't use both cores after all? Why does it have to be a generic kernel, instead of one specialized for your CPU?

Here's my uname -a:
Linux links 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

I haven't seen any guides for a custom kernel in Feisty, and there doesn't seem to be an 64-bit dual core kernel in apt.
The generic kernel supports SMP, and enables correct optimizations for your CPU at boot time so there's no need for any custom kernels for specific CPUs any more.

Anyway, if you are even able to see 2 CPU's that means SMP is working correctly. So if your program only uses one CPU it means the program runs in single thread. Try to find some better program to do the job if you want it to use 2 CPU's ;)

CPUburn only runs on a single thread.

---

### Post by Eddy Dean on 2007-07-26
Sooo... Dual Core is pretty much worthless if you're not heavy multitasking? None of the programs I use seem to be multithreaded, because the CPU usage never gets above 50% (only in games, and I'm sure there are multiple threads in most of the games).
That really, really sucks.
If I would compile those programs with the CFLAGS and CPUTYPE that match my PC, will gcc try to make the program multithreaded/optimized for SMP?

---

### Post by mcduck on 2007-07-26
> **Eddy Dean said:**
> Sooo... Dual Core is pretty much worthless if you're not heavy multitasking? None of the programs I use seem to be multithreaded, because the CPU usage never gets above 50% (only in games, and I'm sure there are multiple threads in most of the games).
That really, really sucks.
If I would compile those programs with the CFLAGS and CPUTYPE that match my PC, will gcc try to make the program multithreaded/optimized for SMP?
No, all programs in ubuntu repositories are already optimized. If the program wasn't written to use multiple threads in the first place there's nothing you can do about it (except rewrite the program). Compiler won't help you there. And many thing people do on their computers simply cannot be broken to multiple threads that easily.

I use Grip to rip CD's, and it supports dualcore (if you enable it in the settings). Also I use mencoder for video format conversions and that seems to use both cores as well.

But yes, you are right that you need to do some multitasking to get any real benefits from dual core. It's not the same as having twice as powerfull single core CPU.

Anyway, at least on my use dual core s a blessing even when programs don't run on both cores. It means that if one app is running at 100% CPU use I still have the other core left to do whatever I want.

---

### Post by Eddy Dean on 2007-07-26
Most things can be broken into multiple threads. Take video conversion for example. You could have one thread assigning small pieces of video to other converting threads, or have one thread start at the end of a video and one at the beginning (that's not possible with all video formats, but anyway). The initialization of programs is also easily split up in threads. One thread for interpreting config files, one for loading the libraries, one for drawing the gui etc etc.

Anyway... It still sucks. I think I would've been better off with one 3,5GHz core, instead of two 2,8GHz cores. I do some multitasking, but hardly ever multiple cpu-intensive programs at the same time.

---

