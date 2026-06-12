---
title: "Thinkpad T22 freezing"
date: 2008-06-23
forum: General Help
---

### Post by Lr5 on 2008-06-23
I have had problems with my thinkpad t22 freezing. For example, it sometimes does it  when remote used with vnc. Now it seems it freezes every time I try to compile a java program.

It seems it isn't an X issue as I use javac with ssh, not from X. I haven't found anything useful by searching other threads, one solved it by editing the xorg.conf but that didn't help in my case.

The laptop is running Ubuntu 8.04, latest (-19) kernel. Anyone knows what could help, or similar problems?

---

### Post by kerry_s on 2008-06-23
what are the specs?

---

### Post by tgalati4 on 2008-06-23
Sometimes reseating the memory cards helps.  Try running memtest overnight for 30 complete cycles.  At least that would rule out RAM as a problem.  With portables that old, could be a heat issue causing the motherboard to freeze.

---

### Post by Lr5 on 2008-06-23
> **kerry_s said:**
> what are the specs?

1 GHz Pentium III processor, 256MB ram, 32 GB hard disk, 86C270-294 Savage/IX-MV graphics card.

---

### Post by kerry_s on 2008-06-23
> **Lr5 said:**
> 1 GHz Pentium III processor, 256MB ram, 32 GB hard disk, 86C270-294 Savage/IX-MV graphics card.

256mb and gnome, of course it's freezing, most likely swapping to swap.

---

### Post by Lr5 on 2008-06-23
It has frozen without using the gui too, the javac crashes have happened over ssh. The gui is running though, but it works fine on my older t21 laptop which runs Ubuntu 7.10.

Maybe the problem could be swap related though? Anyone knows how to check that?

---

### Post by kerry_s on 2008-06-23
> **Lr5 said:**
> It has frozen without using the gui too, the javac crashes have happened over ssh. The gui is running though, but it works fine on my older t21 laptop which runs Ubuntu 7.10.

Maybe the problem could be swap related though? Anyone knows how to check that?

try looking in top and see how it's using the memory.
my moneys on hardy, if you can't find a fix try dropping back down to 7.10.

---

### Post by Lr5 on 2008-06-23
Looks like it's using almost all memory when it's running some programs, I think I should try to find out how to check if the swap partition is working correctly.

---

### Post by Lr5 on 2008-06-24
Some of the swap is being used, so at least it can access it. Running memory tests didn't give any results either. Dropping to 7.10 sounds like the best option this far.

---

