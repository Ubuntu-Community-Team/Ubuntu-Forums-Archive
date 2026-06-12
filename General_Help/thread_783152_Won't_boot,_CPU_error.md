---
title: "Won't boot, CPU error"
date: 2008-05-05
forum: General Help
---

### Post by vonn on 2008-05-05
When I try to boot my Linux drive; ubuntu 8.04 boot screen, it seems like it's fine. But once the loading bar fills it comes up with an error that says the cpu stopped - 11 seconds. 
I can boot my windows drive and my other drives fine. I can even take the ubuntu drive out, put it in a different computer, and boot that. 

Three questions.

Why and what does that error mean?
How do I stop it so I can make finally make the switch from windows to Linux?

---

### Post by vonn on 2008-05-05
Anyone?

---

### Post by haiji on 2008-05-05
have you tried to boot in safe mode?

---

### Post by vonn on 2008-05-05
Yes. And repair mode. I get the same error

---

### Post by Leesh on 2008-05-05
> **vonn said:**
> When I try to boot my Linux drive; ubuntu 8.04 boot screen, it seems like it's fine. But once the loading bar fills it comes up with an error that says the cpu stopped - 11 seconds. 
I can boot my windows drive and my other drives fine. I can even take the ubuntu drive out, put it in a different computer, and boot that. 

Three questions.

Why and what does that error mean?
How do I stop it so I can make finally make the switch from windows to Linux?
Here are some questions:
1) What CPU do you have?
2) Have you ever tried to install other Linux distributions on this machine?

Please, if it is not so hard, write the complete error report that is given on the screen when the error appears.

---

### Post by wirelessmonkey on 2008-05-05
Nevermind, I've got to learn to refresh pages before replying.

---

### Post by vonn on 2008-05-05
I'm running an Intel p4 HT 3.6gz
I have not. This Linux wasn't installed on this machine. It was installed on my lesser box which is running a p4 2.6gz

---

### Post by Leesh on 2008-05-05
> **vonn said:**
> I'm running an Intel p4 HT 3.6gz
I have not. This Linux wasn't installed on this machine. It was installed on my lesser box which is running a p4 2.6gz
Seems like the OS can't handle some of the CPU commands. If the system wasn't installed on this machine, then try to reinstall it on your machine, because the problem may be in the Hyper Threading (you installed the system on a machine without HT, and trying to boot on a machine with HT - this might be the problem, because some of the CPU features can't be correctly interpreted).

---

