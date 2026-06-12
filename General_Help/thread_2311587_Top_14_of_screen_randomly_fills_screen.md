---
title: "Top 1/4 of screen randomly fills screen"
date: 2016-01-28
forum: General Help
---

### Post by GQDQALC on 2016-01-28
Hi all. I'm Ubuntu 14.04 LTS on Samsung ATIV Book 9, graphics card is Intel Corporation Broadwell-U Integrated Graphics (rev 09). I find that occasionally the screen randomly changes so that the top 1/4g fills my entire computer screen. When this happens I can still click and interact within the part of the screen shown. xrandr -s 0 and xrandr --fbmm <various sizes> don't seem to help. Any ideas on what's going on?

---

### Post by ajgreeny on 2016-01-28
What output do you get from xrandr when the screen is showing just that quarter; does it still show the expected full resolution or the truncated vertical resolution?

---

### Post by GQDQALC on 2016-01-29
Thanks for your response! It shows the expected full resolution which leads me to believe for some reason the OS thinks the screen is bigger than it is. However using fbmm doesn't seem to do anything

---

### Post by ajgreeny on 2016-01-29
It all seems to point to a hardware fault, in my opinion.

---

### Post by GQDQALC on 2016-02-02
Uh oh - that's interesting. Do you have any idea what the nature of the fault might be or whether it might make my computer unusable? Rebooting solves the problem but it's fairly unpredictable when it happens. Why would doing xrandr --fbmm <1/4 size> not fix it?

---

### Post by Vladlenin5000 on 2016-02-02
> **ajgreeny said:**
> It all seems to point to a hardware fault, in my opinion.
+1

> **GQDQALC said:**
> Uh oh - that's interesting. Do you have any idea what the nature of the fault might be or whether it might make my computer unusable? Rebooting solves the problem but it's fairly unpredictable when it happens. Why would doing xrandr --fbmm <1/4 size> not fix it?

Graphics chip and/or the panel itself. Hardware failures can't be correct by software.

---

### Post by GQDQALC on 2016-03-02
Figured this out - this can be solved by restarting the x-server (ctrl-shift-backspace on my computer)

---

