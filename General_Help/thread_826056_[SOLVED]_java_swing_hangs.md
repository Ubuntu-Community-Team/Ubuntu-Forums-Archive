---
title: "[SOLVED] java swing hangs"
date: 2008-06-11
forum: General Help
---

### Post by tERn on 2008-06-11
Hey guys

Im using ubuntu hardy, im also have a radeon 9250 card. I dont know why my swing isnt working. When i run a java program that contains a java swing frame, the program just hangs (the screen becomes black like when my computer is working hard). So then usaully i just abort the program. I have access to a remote machine that supports ssh -X, so i tried to run my program via ssh -X and the use their ecclipse, and the program worked fine. I am using the same compiler version for my eclipse (1.6) as that machine. Programs that doesnt contains swing runs perfect. JRE and JDK is updated.
Thank you.

---

### Post by Pjotr123 on 2008-06-11
Completely remove OpenJDK and switch entirely to Sun Java 6 JRE:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

---

### Post by tERn on 2008-06-11
Yea thanks, its fixed now, the problem was the eclipse didnt know where jre 1.6 was installed. I thought it automaticly updates when i installed it.

---

