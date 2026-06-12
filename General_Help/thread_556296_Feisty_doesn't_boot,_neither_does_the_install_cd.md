---
title: "Feisty doesn't boot, neither does the install cd"
date: 2007-09-21
forum: General Help
---

### Post by NCLI on 2007-09-21
I installed Feisty a few minutes ago, totally clean install, after formatting my HDD. However, when I start my laptop, it doesnt even open Grub. After the OS boot screen, it just displays a blank screen with a blinking cursor in the top left corner, nothing else. 

If I try to boot from the install cd, it does the same thing. I installed the 32 bit version.

CPU/ AMD Turion 64 X2 1.60 GHz
GPU/ Geforce 7400.

---

### Post by nvteighen on 2007-09-21
Having an AMD Turion 64, you should use the 64-bit, I think.

---

### Post by NCLI on 2007-09-21
Well, my XP was 32-bit, so I don't see the problem.

Also, could such a mistake screw-up the entire boot process, and prevent me from starting the install cd?

---

### Post by nvteighen on 2007-09-21
> **NCLI said:**
> Well, my XP was 32-bit, so I don't see the problem.

Also, could such a mistake screw-up the entire boot process, and prevent me from starting the install cd?
Actually, I don't know, but it is what I would have done from the beginning knowing that I have that processor ;) (I've always been 32-bit...). It's the logical solution; if that doesn't work, then you have a serious hardware problem.

And, are you sure your XP was 32-bit?

---

### Post by NCLI on 2007-09-21
> **nvteighen said:**
> Actually, I don't know, but it is what I would have done from the beginning knowing that I have that processor ;) (I've always been 32-bit...). It's the logical solution; if that doesn't work, then you have a serious hardware problem.

And, are you sure your XP was 32-bit?

Yes, very. I was also surprised.

I guess I'll try to install the 64-bit version, unless someone else has a better idea?:confused:

---

### Post by nacho32 on 2007-09-21
I have a Amd +3500 64 cpu
on my desktop running a triple boot XP, pro 32 bit, Vista Ultimate, 32 bit and Ubuntu, 32 bit ,
they all run fine, since a 64 bit is backward compatible. in most cases..


to me it sounds like you problem lies in booting off the HD first.

make sure when your pc boots up in your bios  the cd- dvd  drives boot first. Or it will lead to problems witch sound like yours. 

another thing you will want to do is download the super grub boot loader iso,, burn that to a cd very handy to see if the boot loader is even loaded .
good luck and happy computing.

---

### Post by NCLI on 2007-09-21
> **nacho32 said:**
> I have a Amd +3500 64 cpu
on my desktop running a triple boot XP, pro 32 bit, Vista Ultimate, 32 bit and Ubuntu, 32 bit ,
they all run fine, since a 64 bit is backward compatible. in most cases..


to me it sounds like you problem lies in booting off the HD first.

make sure when your pc boots up in your bios  the cd- dvd  drives boot first. Or it will lead to problems witch sound like yours. 

another thing you will want to do is download the super grub boot loader iso,, burn that to a cd very handy to see if the boot loader is even loaded .
good luck and happy computing.

That sounds more like it, I'll go try that now

---

### Post by NCLI on 2007-09-21
Sorry about the double-post, but it still doesn't work, it doesn't even load the cd. The DVD-drive is set as first boot device in the BIOS config.

Any other ideas, guys? I'm getting rather deperate.

---

### Post by NCLI on 2007-09-21
"bump," sorry.

I'm starting to suspect it could be my boot options, but I restored the system default and they look fine...

---

