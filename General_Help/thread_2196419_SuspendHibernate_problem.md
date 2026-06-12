---
title: "Suspend/Hibernate problem"
date: 2013-12-29
forum: General Help
---

### Post by hyyhyyyy123 on 2013-12-29
MY laptop has been having problems resuming from suspension, and both workarounds used in [http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290) do not work on my system. When I put my session into suspend and try to bring it back, it leaves me with a lit black screen and I have to hard reboot to get it to work again. 

I'm running ubuntu 12.04 64-bit

---

### Post by hyyhyyyy123 on 2013-12-29
Also, here's some info I got from uname -a 

     Linux nig-AO725 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ajgreeny on 2013-12-29
Try installing a later kernel, both the 3.5.0- and 3.8.0- series are available to 12.04, and one or other may help you overcome this problem.

---

### Post by hyyhyyyy123 on 2013-12-29
How do I do that? Sorry, noob here.

---

### Post by ajgreeny on 2013-12-29
I suggest you install synaptic first which is a lot more flexible than the software-centre (sudo apt-get install synaptic) then using that search for 3.5.0-44 which is the latest of the 3.5 series, and install that plus the same version header packages (2 of them).

I do not know if this will solve your problem, but it can often help with those difficulties.

---

