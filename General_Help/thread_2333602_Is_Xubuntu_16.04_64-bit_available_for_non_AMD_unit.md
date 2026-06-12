---
title: "Is Xubuntu 16.04 64-bit available for non AMD units"
date: 2016-08-11
forum: General Help
---

### Post by s9032g@comcast.net on 2016-08-11
Is Xubuntu 16.04 LTS 64-bit only available for AMD using computers? That seems strange.

---

### Post by wildmanne39 on 2016-08-11
No, on the site it says AMD64 but that one is also for intel, I am currently running it on an intel myself.

---

### Post by QIII on 2016-08-11
"AMD64" is a historical accident.  AMD was the first to bring 64 bit architecture to the consumer market, so it was called AMD64.  Intel uses exactly (except a few esoteric cases) the same 64 bit architecture and instruction set.

It is often now referred to as x86_64 or x86-64.

---

### Post by grahammechanical on 2016-08-11
amd64 is the 64 bit version of Ubuntu/Xubuntu that runs on 64 bit CPUs made by both AMD & Intel. i386 is the 32 bit version of Ubuntu/Xubuntu that runs on 32 bit CPUs made by both Intel & AMD. And because the architecture of 64 bit CPUs is backwards compatible with the architecture of 32 bit CPUs the i386 version will also run on 64 bit Intel & AMD CPUs.

Why i386 & amd64? It was the Linux developers that made that decision.  The Intel 80386 was the first Intel 32 bit CPU. So, the Linux developers called 32 bit Linux i386. AMD produced a 32 bit CPU that was compatible with the Intel 80386 and so Linux i386 could also run on AMD 32 bit CPUs.

AMD was first to extend their 32 bit CPU design into a 64 bit CPU. So, the Linux developers called 64 bit Linux amd64. And so, 64 bit Linux (amd64) also runs on Intel 64 bit CPUs.

Regards

---

### Post by Geoffrey_Arndt on 2016-08-11
Really no good excuse not to update the name . . . what would it cost?  (i386-64-al or 1386_64_amdintel).

---

### Post by QIII on 2016-08-11
Why bother?  That's the common name.

But if you want to seek out every instance and change it, maybe someone would let you do that.  Oh.  Also find all the code where it appears, etc ...

---

### Post by Geoffrey_Arndt on 2016-08-11
The past is past.   But future releases need not be ambiguous by design.   Just too much German in me, . . . need logic, order and korrectness.

But as a German General once said . . . . "Situation Hopeless, , , , but not Serious"

---

### Post by QIII on 2016-08-12
There is no ambiguity.

---

### Post by mastablasta on 2016-08-12
x86 or 366 is on the other hand intel's designation of CPU. So as an AMD CPU user i would be confused by it. :P

---

### Post by s9032g@comcast.net on 2016-08-14
Judging by the number of people inquiring on line because they are confused by the AMD it's past time to simplify (update) the terminology.

---

### Post by PaulW2U on 2016-08-14
> **s9032g@comcast.net said:**
> Judging by the number of people inquiring on line because they are confused by the AMD it's past time to simplify (update) the terminology.Although I might have once agreed with you, a quick look at some of the Ubuntu download pages shows only references to 32-bit or 64-bit software. I wonder how many "average" users will actually be aware of which company manufactured their processor.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

I see the same at openSUSE and Fedora, no reference to the chip manufacturer at all, just links to either 32-bit or 64-bit downloads with 64-bit now being the default.

---

### Post by deadflowr on 2016-08-14
If anything, they need to dump the i386.
That particular arch is not even supported in the kernel anymore, except the version used in 12.04.1...

---

### Post by kibohusky on 2016-08-14
The AMD64 label is fine, most users just see the numbers 64 and go for that and not even pay attention to the AMD part.

---

