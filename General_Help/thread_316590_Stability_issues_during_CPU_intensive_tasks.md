---
title: "Stability issues during CPU intensive tasks"
date: 2006-12-11
forum: General Help
---

### Post by mupham on 2006-12-11
Hi,
  I installed Ubuntu 6.10 for the first time 2 days ago (Very easy install by the way).  Ever since I've a lot of programs crashing unexpectedly.  It seems to occur more often during tasks which a lot of CPU.  For example when compiling the kernel, I get a core dump from gcc about a minute into the process.  Similar crashes occur when encoding video or audio.  I've even had the whole machine lock up a few times.

  I do have Debian 3.1 (kernel 2.6.8) also running on this same box and it has been very stable for about a year now I suppose.  I also ran the MemTest86 for a few hours (to convince myself that it wasn't hardware).  lsmod showed a lot of ACPI related modules loaded that I don't see in Debian.  I really don't know a lot about the kernel, but could that be causing my issues?  Are there any good resources on how to troubleshoot these farther?  

Thank you,
Mike

---

### Post by mupham on 2006-12-17
Update:

I believe that the CPU was the culprit in my case.  I had an overclocked AMD Barton 2500+ to 3200+ which I never had an issue with for over three years in Windows or Linux.  I installed the cpuburn package and ran the burnK7 program and of course my machine would freeze after a few minutes.  I've since scaled back on the FSB and the machine has been working great since.  It's curious though that I can still boot into Debian and have no problems with the overclocked CPU.  I wonder if this kernel has more K7 Optimizations that tax the CPU a little more.

Aside from this self-inflicted problem, I'm really impressed so far with the Ubuntu distribution.  I'm going to be moving all of my stuff over in the upcoming days.

Regards,
Mike

---

