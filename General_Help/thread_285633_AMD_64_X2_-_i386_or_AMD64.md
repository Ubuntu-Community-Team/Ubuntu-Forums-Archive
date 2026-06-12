---
title: "AMD 64 X2 - i386 or AMD64?"
date: 2006-10-27
forum: General Help
---

### Post by carlos1 on 2006-10-27
Up to now I've been running Ubuntu (and before that, Fedora) on intel boxes and on one AMD Athlon 4 laptop.
I'm about to buy an AMD 64 X2 machine.
I want to run Kubuntu 6.10 on it, and especially use it as a multimedia box (as well as for other everyday computing.)
My question is, can and should I run the normal i386 kernel, or do I have to run the AMD64 one, and aren't there drawbacks to the 64-bit one, ie. low availability of software? 
I searched the forum and all I could find was something about running a k8 kernel, but no info to start with.
If I run the i386 flavour, will I get good performance from the proc and take advantage of the dual cores? 
Any pointers on this, or pros and cons would be appreciated. Thanks.

---

### Post by matthewstory on 2006-10-27
I've only ever done this with debian, but with debian i used the i386 version, works fine.

---

### Post by stylishpants on 2006-10-27
With 64-bit hardware, you will have a choice of running 32 bit or 64 bit Ubuntu.

If you choose 32 bit Ubuntu, you should install the K8 kernel image (package linux-amd64-k8).  You will get multi-core support, and this kernel is tuned to work well for your CPU.

If you choose 64 bit Ubuntu, it is true that you will pay a bit of a price in less software availability.  You will not notice much of a speed difference from 32 bit either.  On my own amd 64 X2 machine, I found that 64 bit Ubuntu seemed faster at opening and reading large (1+ gigabyte) files.  Apart from that, there was no noticeable difference for me.

---

### Post by dcstar on 2006-10-27
> **carlos1 said:**
> Up to now I've been running Ubuntu (and before that, Fedora) on intel boxes and on one AMD Athlon 4 laptop.
I'm about to buy an AMD 64 X2 machine.
.......
Any pointers on this, or pros and cons would be appreciated. Thanks.

If you have any AMD CPU you should use the K7 kernel, and then possibly the 64 bit one if you like.

---

### Post by carlos1 on 2006-10-27
Thanks, I really appreciate the advice.
So, if I download and use the AMD64.iso, would I get a 32-bit version out of that, and does it include an option on install to select the k7 or k8 kernel image, or is that something I have to do after initial install? 
Also, k7 or k8? What would be the difference?
Sorry if this is posted somewhere else already, I couldn't find it. Many thanks.

---

### Post by carlos1 on 2006-10-27
OK, so I will install the 32-bit version on AMD 64 X2. 

Which .iso do I use to do that - i386 or AMD64?

---

### Post by handy on 2006-10-27
> **carlos1 said:**
> OK, so I will install the 32-bit version on AMD 64 X2. 

Which .iso do I use to do that - i386 or AMD64?

[URL="http://ubuntuforums.org/showthread.php?t=284808"]Good move to go i386 32bit  

Download links on this page...[/URL]

All the best! :)

---

### Post by kuja on 2006-10-28
You've got a choice. 
64-bit strengths:
-Certain apps are much faster (Rendering, Encoding, Complex Math, stuff like that)
-32-bit apps can still be installed

64-bit weaknesses:
- slightly smaller package availability
- some, especially commercial, programs are not available at all for 64-bit. Most of them have a work-around, but some more obscure ones don't.

If you take the 64-bit you'll likely lose a little bit of time to getting things up and running, but beyond that everything is smooth. Best of luck.

---

### Post by handy on 2006-10-28
64bit is much more suitable for experienced users, who have a use for it.

I've run both, & there was absolutely no benefit for me, only disadvantages  in 64bit, due to added difficulty in setting up.

---

### Post by Pinoy915 on 2006-10-28
I'll have to agree. For beginning users, I would use i386 version. Ubuntu 64 is nice to use but if you're not using it for what's it designed for (i.e. very large memory access, complex math, 64 bit instructions, etc.) then it's more difficult to setup. In Edgy, you won't have to choose any kernels as there is only generic available in Edgy. SMP support worked for me right out of the box.

---

