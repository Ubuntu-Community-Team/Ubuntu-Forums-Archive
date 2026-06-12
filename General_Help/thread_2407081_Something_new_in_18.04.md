---
title: "Something new in 18.04"
date: 2018-11-29
forum: General Help
---

### Post by Lloydb39 on 2018-11-29
I've never had Ubuntu lock up on me before but it does with 18.04. Last time, I had several tabs open in chrome and tried to open LibreOffice and everything froze. I could open a terminal but I forgot the command to find and kill processes, so I just shut it down. Is this a thing? Is there something I could do to troubleshoot?
Using on homebuilt AMD-64 with 8 gigs of memory.

---

### Post by Autodave on 2018-11-29
5 machines here running 18.04 and no problems at all.  You certainly enough enough RAM.  What video card are you running and did you install any driver for it? If so, what one and where did you get it from?

Off hand, my first thought is an overheating problem.  Having several tabs open on Chrome could be enough to stress the CPU: especially if the GPU doesn't have the correct driver installed.

---

### Post by oldos2er on 2018-11-29
Please tell us your hardware specs, and whether you're running a laptop or desktop. 

You can try running memtest on your RAM and smartctl on your disks.

---

### Post by Lloydb39 on 2018-12-04
Homebuilt desktop AMD 64 with 8 gigs of memory, no video card. ASUS motherboard. It just did it again. This time, stuck while trying to quit Thunderbird. Is the terminal commend "sudo shutdown"?

---

### Post by Dennis N on 2018-12-04
Just saying that it's has an AMD processor and Asus board doesn't help that much. Which processor model? And is this a new computer build? If so, you may just need to obtain a newer kernel.

---

### Post by Lloydb39 on 2018-12-04
AMD FX)-4100 Quad-Core Processor. I built it about 5-6 years ago, I think.  The software just updated again today. It updates frequently.

---

