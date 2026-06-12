---
title: "Confusion about df command in manual"
date: 2014-04-09
forum: General Help
---

### Post by GirishSharma on 2014-04-09
Learning Ubuntu 13.0.04 64 bit on VM

I am reading below text when I said :
man df 
"..... This version of df cannot show the space available on unmounted file systems, because on most kinds of systems doing  so  requires very nonportable intimate knowledge of file system structures."

... "doing  so  requires very nonportable intimate knowledge" what is actual meaning of this sentence, kindly elaborate.

Thanks and Regards
Girish Sharma

---

### Post by sudodus on 2014-04-09
I think it means that there is no standard method to show the space available on unmounted file systems.

'Nonportable intimate knowledge' means to me that you would need different methods for different file systems, methods that need very detailed knowledge about that file system, and that won't work with other file systems.

The solution is to mount the file system, run ***df***, and if you wish, unmount the file system again.

---

### Post by GirishSharma on 2014-04-09
Thanks for explanation.

Regards
Girish Sharma

---

### Post by sudodus on 2014-04-09
You are welcome, and good luck learning about linux :KS

---

