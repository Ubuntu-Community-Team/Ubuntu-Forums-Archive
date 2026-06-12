---
title: "Feisty slowing down (temporarily, but annoyingly)"
date: 2007-05-06
forum: General Help
---

### Post by Edricson on 2007-05-06
Hi,

I understand this may be a silly one...

On Dapper, which I had been using until last week, I was able to keep quite a lot of stuff open - like Opera, Kile, KDVI, Writer and a couple of small apps running at the same time, with excellent performance.

Now I have upgraded to Feisty, and sometimes the computer... well, it doesn't exactly freeze, but it slows down and takes quite some time to resume normal operation. Interestingly, the System Monitor doesn't show significant CPU activity - which is clearly there, to judge by the fact that even the mouse responds torturingly slow.  Sometimes it can go on for as long as ten minutes, and it's very annoying. And it can start when I only have, say, only Opera and Writer running - which was no problem at all on Dapper.

For the record, I'm on a Samsung X20 with a 1,4 GHz Celeron CPU and 512 MB RAM.

And I'm not too good at it, so I don't even know where to start. I understand this is not an issue with my computer not being up to the task in terms of hardware... or is it? (that would be not nice)

Thanks for any help!

---

### Post by rai4shu2 on 2007-05-06
Even with the CPU maxed out, it seems unlikely for the mouse to be affected. This sounds more to me like a video or video driver problem.

---

### Post by Edricson on 2007-05-06
Thanks for the reply!

Hmm, I hadn't thought about it (the mouse is technically a touchpad, but I'm not sure if it matters)

How would I go about checking it? Strange it could be a driver issue if it was working perfectly on Dapper...

---

### Post by aidanr on 2007-05-06
is system monitor showing all tasks or just yours? you can also run top in a terminal to see what's eating up the cpu, my guess is some cron job

---

### Post by rai4shu2 on 2007-05-06
I assume it has the ATI Mobility Radeon X600 128 MB video card and that you are using the fglrx driver?

Sorry, I don't know much about ATI.

---

### Post by Edricson on 2007-05-06
> **aidanr said:**
> is system monitor showing all tasks or just yours? you can also run top in a terminal to see what's eating up the cpu, my guess is some cron job

Umm, that's what I thought, too; however, system monitor showing all tasks doesn't have anythung suspicious. Running anything in a terminal is not feasible: when the system works, it works, when it doesn't, I can't move the mouse, let alone start the terminal or type anything.

---

### Post by Edricson on 2007-05-06
> **rai4shu2 said:**
> I assume it has the ATI Mobility Radeon X600 128 MB video card and that you are using the fglrx driver?

Sorry, I don't know much about ATI.

Nope, I was using Xorg; I've installed fglrx, let's see if it's going to help.

Though fglrx-info shows the following output:

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2

---

### Post by Edricson on 2007-05-08
Thanks! After installing fglrx the problem has gone away.

---

