---
title: "Can desktop effects work without xserver-xgl ?"
date: 2008-06-27
forum: General Help
---

### Post by FFighter on 2008-06-27
Well, xserver-xgl package is not instaled on my system and desktop effects is working fine. How could that be?

Btw, is dekstop effects just an abstraction over compiz os is it a fork of compiz?

Thanks in advance!

---

### Post by Forlong on 2008-06-27
> **FFighter said:**
> Well, xserver-xgl package is not instaled on my system and desktop effects is working fine. How could that be?
Xgl is pretty much obsolete on Hardy -- Intel and ATI chips work with AIGLX and Nvidia's proprietary driver has it's own rendering method.
> **FFighter said:**
> Btw, is dekstop effects just an abstraction over compiz os is it a fork of compiz?
The so-called Desktop Effects **are** Compiz (plus the official Compiz Fusion plugins).

---

### Post by tornado89 on 2008-06-27
On Ubuntu Hardy.. ATI Can Run Compiz + Fusion ( Advanced Desktop Effects ) Without Using XGL ..

It Can Render The Effects On Its Own Now ...

---

### Post by FFighter on 2008-06-29
Well... desktop effects just stopped working again and it won't start. I think it will only work if I install xserver-xgl. However, this screws up my keyboard layout and I also found out that Compiz is sucking too much CPU power that it just doesn't worth using.

I have found that my graphics chip, Intel 965 has been blacklisted, so that is probably the reason I'm going through so many problems while trying to have a smooth Compiz experience. Really bad luck of mine, seems I will have to wait for 8.10 for official support for my graphics chip.

*sigh*

---

