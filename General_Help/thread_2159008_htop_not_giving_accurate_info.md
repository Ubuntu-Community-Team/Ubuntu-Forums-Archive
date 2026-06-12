---
title: "htop not giving accurate info"
date: 2013-07-01
forum: General Help
---

### Post by Marcelo Ruiz on 2013-07-01
Hi, I have a question about htop. When I run on a core i7 it I see in the graphic part one CPU running at 100% (my laptop fan is running like crazy, so the condition exists) but in the process list none of them is using more than 3% of CPU.
Is there any way to get an accurate list of the processes running in my computer to know which is causing the problem?

---

### Post by Marcelo Ruiz on 2013-07-01
ok, I found the culprit: apport
I used nmon to get the info. Somehow htop was not showing apport at all...

---

