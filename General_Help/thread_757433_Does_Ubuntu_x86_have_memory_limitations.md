---
title: "Does Ubuntu x86 have memory limitations?"
date: 2008-04-16
forum: General Help
---

### Post by bdoe on 2008-04-16
I know that 32-bit Windows cannot address 4GB of memory, likely because of how the virtual memory manager handles non-traditional memory such as on video cards.  Does Ubuntu have this same limitation?
 
Here's my proposed scenario:
I have a Intel C2D-based laptop with 4GB of DDR2 memory.  According to my math, 4GB is the absolute max that a 32-bit system can address. Am I able to install and run 32-bit Ubuntu on this thing as configured? Or am I going to have to run the 64-bit version?
 
Sorry for the silly question.  I'm just not too enthusiastic about having to run a 64-bit OS given the abysmal driver support they generally have.

---

### Post by sekinto on 2008-04-16
You are correct, on a 32bit system you can only make use of 4GB of RAM, I think the limitation for a 64bit system is 16EB (is that the correct abriviation for exebytes?), although usually there are limitations in the OS but they are still extremely high.

Even though a 32bit OS can handle 4GB I would still go with 64bit if I had the option.

---

### Post by AnRa on 2008-04-17
You should try using [linux-image-server]("apt://linux-image-server") (32 bits) as it supports more than 4 GiB of RAM using [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension"). :)

---

