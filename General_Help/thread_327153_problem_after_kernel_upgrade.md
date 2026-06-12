---
title: "problem after kernel upgrade"
date: 2006-12-28
forum: General Help
---

### Post by skd5aner on 2006-12-28
Hi, I'm having a problem after I've upgraded the kernel on 6.10 to 2.6.19.1.  I followed the kernel guide on the forums and had no problems.  I recently discovered the issue when I try and do an apt-get:

apt-get install libfaad2-0 libfaad2-devReading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package kernel-headers-2.6.17.3 needs to be reinstalled, but I can't find an archive for it.

I'm not quite sure what to do.  When I try and do an apt-get install kernel-headers-2.6.17.3 it doesn't work either.

Is there someplace I can point it to use the 2.6.19.1 headers or how can I solve this problem?  ](*,)

---

