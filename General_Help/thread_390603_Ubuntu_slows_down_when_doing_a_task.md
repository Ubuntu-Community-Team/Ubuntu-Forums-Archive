---
title: "Ubuntu slows down when doing a task"
date: 2007-03-22
forum: General Help
---

### Post by shironeko on 2007-03-22
When doing something, like converting a video, installing an application or installing updates, Ubuntu slows terribly down.

I wonder If there is a way to avoid this...

I got an AMD 64 3000+ and 512MB RAM, but the RAM memory shouldn't be the problem because it never goes over 350MB. And the processor isn't that bad.
Maybe has swapiness something to do with my issue? It is currently set at 10.

Thank you,

PD. Some additional info:

Ubuntu Edgy Eft 32 bits
Beryl 2.0 + Aiglx
ATI 300X

---

### Post by tommcd on 2007-03-22
Video encoding is very demanding on th CPU. It will likely use 90-100% of the CPU, which can slow things down. Installing software will use a lot of your CPU also, but software installs pretty quickly in linux, so I've never noticed much of a slowdown there.
Run <top> in terminal when the system slows down to see what is using the most CPU cycles. If speed returns after video encoding finishes, and after the software is installed, I probably would not worry about it.

---

