---
title: "using same /home and swap partitions on muiltple installs"
date: 2007-08-07
forum: General Help
---

### Post by Jeffa on 2007-08-07
Hello all. I have a quesiton regarding using the same /home and swap partition for multiple insalls. Here's the situation:

I have a system running 7.04 32bit on a Core 2 Duo 6600. I'd like to install 64bit 7.04 to take full advantage of the processor, but I'd rather not reformat the existing partition and have to reconfigure everything. 

So the question is, can I create a new partition for my /home directory and use that one /home directory for both the 64 and 32 bit installatins? 

Can I also use the same swap partition for both installations? 

Will using the same /home partition keep system settings and configuration the same between the two installations? 

Will the 32 bit vs the 64 bit prevent me from sharing these two partitions between installations? 

Thanks in advance for all the help!

---

### Post by dabl on 2007-08-07
Short answer:

swap = YES
/home = NO

Reason -- /home keeps not only data files but also "settings" related to things you have installed and configured.  Unless you miraculously installed and configured everything identically under OS #2, it will puke when it sees the "settings" in the /home folder from OS #1.

:)

---

### Post by Jeffa on 2007-08-07
Good to know. Thanks!

---

