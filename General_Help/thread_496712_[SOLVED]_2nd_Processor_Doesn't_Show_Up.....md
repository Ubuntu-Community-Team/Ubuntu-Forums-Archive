---
title: "[SOLVED] 2nd Processor Doesn't Show Up...."
date: 2007-07-09
forum: General Help
---

### Post by jumping_snake on 2007-07-09
So I'm not entirely new to Linux, but I'm no pro. I have a Tyan Tiger MP board with two processors on it. Both processors and seen in the BIOS. I initially tried to install Ubuntu 7.04 Desktop on the system, but even after installing the smp kernel, the second cpu wouldn't show up if I sudoed and tried /proc/cpuinfo. I read up on the forums here to see if anyone had had any issues, but the only thing that I could find that someone else tried other then getting the smp kernel was to install Ubuntu 7.04 Server edition. I tried this, but there's still no 2nd processor. Both processors are exactly the same as stats and make. Ideas?

---

### Post by skullmunky on 2007-07-09
you shouldn't need the server edition.  the stock 7.04 install should work; at least, for me it finds both cores on my athlon x2.  

uname -a tells me my kernel is 

2.6.20-15-generic #2 SMP

which is what it installed by default.  check that, just to make sure ...
what kind of processors is that, anyway?

---

### Post by jumping_snake on 2007-07-09
Ok, sweet, at least I'm running close to the same kernel that you are - 2.6.20-16-generic #2 SMP....but still after I do 
% sudo -s
Password:

% cat /proc/cpuinfo

It still only shows a single CPU, is that right?

Also, when I do 
% grep 'processor' /proc/cpuinfo | wc -l 
the system returns 1.

Now if I'm just crazy that the system is fine I'll accept that, but I thought /proc/cpuinfo was supposed to show Processor 0 and Processor 1 if there's two processors?

I thought I should also mention that BOINC only sees one CPU after running it's "CPU Benchmark"

Other ideas?

P.S. Model: AMD Athlon(tm) XP 2400+ Socket A

---

### Post by jumping_snake on 2007-07-10
I was just talking to a friend, does anybody know how the kernel decides which kernel to install? He was thinking that if the kernel reads in the cpu info, sees Athlon XP, it won't try to operate the second cpu.....like not even try to see if it's there?

:guitar:


And another question: Does anyone have a dual Athlon XP (Socket A) setup running Ubuntu?

---

### Post by jumping_snake on 2007-07-16
HOOKAY, so since I'm doing this by myself, I've just decided to try compiling my own kernel. I'll write back to let everyone know if it works! *crosses fingers*

---

### Post by jumping_snake on 2007-08-02
Well, I finally started from scratch and looked at the hardware side of things. It was weird: the BIOS would see the heat/fan rpms of each socket, but the POST screen wouldn't show 2 processors. After digging around on Tyan's site for awhile, I found out that the model of MB that I have only supports dual MPs, not dual XPs. DOH! So now I'm on the market for a set of MPs, but at least this issue is solved....

---

### Post by hdwrguy on 2007-08-02
If this is for a socket 462 processor like an Athlon XP 1800+ there is a hack which converts an XP to an
MP. It involves either cutting or shorting traces on the package. A while back I found it with google.

Good Luck!

---

