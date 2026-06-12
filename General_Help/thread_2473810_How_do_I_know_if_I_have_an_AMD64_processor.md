---
title: "How do I know if I have an AMD64 processor?"
date: 2022-04-14
forum: General Help
---

### Post by Tom_Carr on 2022-04-14
I want to play with the daily build of Jammy.  On the download website it says:

[COLOR=#111111][FONT=Ubuntu]Choose this if you have a computer based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). Choose this if you are at all unsure.

[/FONT][/COLOR]I am using this on two dekstops, a dell optiplex 990, and a dell optiplex 3040.  How do I know if they are AMD64 processors?

---

### Post by deadflowr on 2022-04-14
What are they currently running?

---

### Post by ActionParsnip on 2022-04-14
Check the Dell support site

---

### Post by ajgreeny on 2022-04-14
Do you know what CPU each of them has, and what operating system is being used on them at present?

That aside I think they will both be 64 bit CPUs as they use Intel i5 or i7 which are all 64 bit.

Try them out, though depending on other hardware specs, you may find it better to try one of the other *buntu versions eg, Xubuntu, my choice for many years, Kubuntu, Ubuntu-Mate, Lubuntu etc etc.
To learn more about the various versions available see the sticky thread at [https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676)

---

### Post by ActionParsnip on 2022-04-14
You can boot live USB / CD and run:
```

lscpu | grep -i Arch

```
Should do it

---

### Post by grahammechanical on 2022-04-14
A bit of history as I remember it.

Intel produced the first 32 bit computer processor unit (CPU). It was the Intel 80386 CPU. Later called i386. The 32 bit Linux kernel is marked as i386. AMD was able to design their own CPU that was compatible with the Intel i386 instruction set. This meant that machines with either Intel i396 32 bit CPU's or AMD 32 bit CPU's would run both 32 bit Windows or 32 bit Linux (i386).

Then AMD extended its 32 bit design to become 64 bit. It took Intel a while to produce a 64 bit CPU that had to match the AMD 64 bit instruction set. The 64 bit Linux kernel is marked AMD64 and will run on either Intel or AMD 64 bit CPU's.

All this means that Ubuntu AMD64 will run on both Intel and AMD processors. My laptop has an Intel Core i7-1051OU CPU and the usual Ubuntu 20.04.4 is running on it satisfactory.

By the way, the 64 bit instruction set is backwards compatible with the 32 bit instruction set. So, 32 bit Linux will run on a 64 bit Intel or AMD CPU.

Regards

---

### Post by Tom_Carr on 2022-04-14
I just tried the AMD64  version and it worked fine, so that's it.  Thanks for your help.  I'll close this  thread.

---

### Post by TheFu on 2022-04-14
Run **lscpu**
That tells you everything about the CPU in the current system.
Look at the "Architecture" line.
Ryzen:  Architecture:                    x86_64
Core i5: Architecture:        x86_64

There are 50 other methods, but that command should be available on any Linux.  You can also use **more /proc/cpuinfo **, but that text file is unfiltered for user consumption. Nothing harmful, just raw text.

---

