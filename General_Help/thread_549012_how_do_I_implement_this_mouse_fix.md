---
title: "how do I implement this mouse fix?"
date: 2007-09-12
forum: General Help
---

### Post by gschoppe on 2007-09-12
I've been having the ever-famous KVM + Mouse = crazy motion/clicking issue, but since i have an off brand mouse, none of the standard fixes are working.

I found a post on a forum with some code to suppress the crazyness that seems like a good workaround in my situation, but I have no idea how to use it

here's the link:
[http://www.uwsg.iu.edu/hypermail/linux/kernel/0406.2/1959.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0406.2/1959.html)

can anyone help me implement this workaround on my system?

---

### Post by Koybe on 2007-09-12
There is very less chance this patch will work. It's for a 2.6.7 kernel. I don't know which version of Ubuntu you're using, but it's a long time this kernel isn't used.

---

### Post by gschoppe on 2007-09-12
Unfortunately, I'm using feisty... so, that means Its back to the drawing board.


with xorg.conf's mouse section configured for auto, is there a way to find what driver it's actually using?

---

### Post by gschoppe on 2007-09-17
well, it seems it was belkin's fault... i'm now using an iogear kvm (overpriced at bestbuy, but cheaper than the flip at staples) and the problem just went away.

---

