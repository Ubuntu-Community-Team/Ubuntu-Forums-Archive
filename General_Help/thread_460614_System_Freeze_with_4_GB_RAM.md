---
title: "System Freeze with 4 GB RAM"
date: 2007-05-31
forum: General Help
---

### Post by benford on 2007-05-31
I've been having a terrible amount of hardware trouble trying to get an  LTSP server running. After extensive memtest86+ runs and CPU testing, (esp this method [http://www.ibm.com/developerworks/library/l-hw1/](http://www.ibm.com/developerworks/library/l-hw1/)) and multiple versions of ubuntu (server 6.06, edubuntu 6.061, edubuntu 7.04, x86 and amd64 versions) it seems that either the motherboard or CPU is having trouble.

My motherboard is a Tyan Tiger K8WE (S2877) with 4 x 1 GB registered DDR 400 kingston value ram. When  2/4 are installed, server runs fine without a hitch, even with prolonged CPU intensive tasks, but when all 4 are installed, the server will lock up entirely (due to Kernel Panic) after a few minutes of a CPU intensive task (rapid recompiling or a screen saver does the trick). Any ideas out there about what is most likely wrong? I'm guessing something in the motherboard chipset, since the CPU works fine with 2 GB of RAM installed. I can post lspci output if anyone wants it.

---

### Post by tronica on 2007-05-31
I've heard people having problems with the bios not correctly supporting 4GB of ram, even thought its suppposed to. I would update the bios. Is ubuntu recognizing all 4 GB of ram? Also if i remeber correctly 32 bit cant read 4 GB or memory, so you will definitly need the 64 Bit version for sure.

Also pop in the install disk and run the memtest.

---

### Post by benford on 2007-06-01
I'll go ahead and try a firmware update tomorrow; that's about the last thing I can think of.

Ubuntu recognizes all 4 GB of ram in 64 bit and 32 bit mode (with 32 bit I must use the bigiron kernel). The problem is the consistent crashes at high CPU load, rather than detecting all of the RAM. On 64 bit it will sometimes kernel panic almost immediately, regardless of CPU load (ie, right after uncompressing the kernel from the install CD).

I've run memtest 86+ multiple times. It freezes up when 4 GB are installed, but testing the dimms 2 at a time (2 GB each) it can pass 50+ runs without a problem.

Thanks for the advice

---

