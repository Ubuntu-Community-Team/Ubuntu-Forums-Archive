---
title: "Which Kernel to use for Sempron 3300 64bit?"
date: 2006-10-15
forum: General Help
---

### Post by kalle314 on 2006-10-15
I am a bit confused about this.

I have a Sempron 3300+ 64bit processor, which I am using for 32bit Ubuntu.

I have been using the i386 kernel which was installed by default, but then I read something about k7 being better for Sempron, so I am using the k7 kernel right now.

But when i do "uname -a" I get 
*Linux pasokon1 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686 GNU/Linux*, which seems to indicate that it should be of i686 type.

According to listings on the internet though, it is of "k8" type. (See for example [http://balusc.xs4all.nl/srv/har-cpu-amd-k8.php](http://balusc.xs4all.nl/srv/har-cpu-amd-k8.php) )
Should I compile my own kernel for k8 architecture instead? 

EDIT: I found out that k8-kernels only should be used for 64bit-ubuntu, and k7 should indeed be the best.

---

