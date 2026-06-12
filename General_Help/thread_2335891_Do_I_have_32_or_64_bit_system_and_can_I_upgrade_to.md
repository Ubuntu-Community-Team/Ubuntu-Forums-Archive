---
title: "Do I have 32 or 64 bit system and can I upgrade to 14.04 64 bit?"
date: 2016-09-02
forum: General Help
---

### Post by Bobby_James on 2016-09-02
Hello,

I have always assumed I had a 32-bit system. This is because lscpu shows:

```
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit

```

I thought that the "Architecture" indicated the hardware but now I understand that it references the kernel (software).

Therefore, since my CPU can handle 64 bit programs, can I upgrade / replace the current 32 bit kernel with that of 14.04 64 bits? If so, what is the safest method?

Thanks!

---

### Post by howefield on 2016-09-02
You are correct about the Architecture referring to the software installed.

There is no way to upgrade to 64 bit short of a clean install of the full operating system.

---

### Post by Bobby_James on 2016-09-03
Fair enough. I understand. But, to clarify, my impression is that I've "always" had a 64 bit system (as the CPU can handle 64 bits) but for some reason I didn't know this and hence always installed 32 bit Ubuntu!

However, I don't understand the Download page ([http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)) which states that:

[64-bit PC (AMD64) desktop image]("http://releases.ubuntu.com/14.04/ubuntu-14.04.5-desktop-amd64.iso")  Choose this to take full advantage of computers based on the  AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core  2).  If you have a non-64-bit processor made by AMD, or if you need full  support for 32-bit code, use the i386 images instead.  Choose this if  you are at all unsure.
[32-bit PC (i386) desktop image]("http://releases.ubuntu.com/14.04/ubuntu-14.04.5-desktop-i386.iso")  
For almost all PCs.  This includes most machines with  Intel/AMD/etc type processors and almost all computers that run  Microsoft Windows, as well as newer Apple Macintosh systems based on  Intel processors.
[COLOR=#000000]
  Why would it say that 32 bit is for "almost all PCs" if the CPU of said PCs can, in fact, handle 64-bit kernels?
[/COLOR]

---

### Post by howefield on 2016-09-03
> **Bobby_James said:**
> ..  Why would it say that 32 bit is for "almost all PCs" if the CPU of said PCs can, in fact, handle 64-bit kernels?

Perhaps because it is for "almost all PCs"...

32 bit can be installed on both 32 bit and 64 bit machines, hence it is suitable as described.

The cpu although highly important, isn't the only defining factor in whether or not 64 bit is good/best for your machine.

---

### Post by Bobby_James on 2016-09-03
Yes, point taken. What would be the other factors? Or, to put it in another way: with a reasonably modern PC, why would one not want to use 64 bit software?

Thanks!

---

### Post by howefield on 2016-09-03
> **Bobby_James said:**
> Yes, point taken. What would be the other factors? Or, to put it in another way: with a reasonably modern PC, why would one not want to use 64 bit software?

What might constitute reasonably modern might be different to you than it is for me, or anyone else, but by most definitions I'd guess relatively few "reasonably modern PCs" would be incapable of running 64 bit.

There are many machines currently being used that are 64 capable but light on RAM, there is a RAM overhead in using 64 bit vs 32 bit.

Software may also be a consideration although that to be fair is almost a non issue these days.

---

