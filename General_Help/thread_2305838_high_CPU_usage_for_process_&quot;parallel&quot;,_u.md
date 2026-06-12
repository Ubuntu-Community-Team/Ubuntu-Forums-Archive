---
title: "high CPU usage for process &quot;parallel&quot;, user lp; printer not working"
date: 2015-12-09
forum: General Help
---

### Post by michael-h-williamson on 2015-12-09
Hi, I have a printer problem question. 
I am using Ubuntu 14.04 32-bit on a Dell Inspiron. It has a expansion DB25 parallel port PCI express card is installed for use with a HP 4050 printer with IEEE 1284 36-pin connector. The printer is detected with the administration GUI, and has worked printing at least a few pages. Mostly it does not work however, with print job status indicating 'pending' or 'held'. Attempting to 'resume' or somehow flush the jobs is unsuccessful, using either the Ubuntu GUI or CUPS at localhost:631. There is a process named "parallel" with very high CPU usage, continuously. The owner is 'lp'. 
How do I determine what is wrong?

Thanks,
-Mike

I am replying to my own thread with a follow-up. 
Doing this:

 # cat file > /dev/lp0

hangs indefinitely, with high CPU usage.
Also, next I am going to try a USB to IEEE 1284 converter cord, as an alternative to the PCIe card.

---

