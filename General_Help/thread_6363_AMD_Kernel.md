---
title: "AMD Kernel"
date: 2004-11-27
forum: General Help
---

### Post by elder68 on 2004-11-27
The machine that I have Ubuntu installed on is an AMD/Duron. Would there be any particular benefit in downloading and installiing the  following: "linux-k7" which I believe is for any AMD Processors. Previously I have had Xandros and Suse 9.0 on this machine and Ubuntu seems to be a bit slow.

Thank you,

Bill.

---

### Post by jdong on 2004-11-27
Search the forum.

A while ago we had this discussion, and two themes arose:

1. k7's are Athlon-XP's. That's what the kernel is compiled for. However, enough people with Durons have used this kernel without issues, so we can assume this is "safe" to do!

2. No performance improvements have been noticed. In fact, the original author of the discussion noted performance *decrease* compared to the i686/i386 kernels. This is *possibly* attributed to the fact that only Athlon XP's benefit from the optimizations in that kernel.


So basically, I recommend that you use an i686 kernel.

---

### Post by elder68 on 2004-11-28
Thank you for this, I guess I will leave things alone. I did make a mistake though, it is an AMD/Athlon that I have.

Bill.

[QUOTE=jdong]Search the forum.

A while ago we had this discussion, and two themes arose:

1. k7's are Athlon-XP's. That's what the kernel is compiled for. However, enough people with Durons have used this kernel without issues, so we can assume this is "safe" to do!

2. No performance improvements have been noticed. In fact, the original author of the discussion noted performance *decrease* compared to the i686/i386 kernels. This is *possibly* attributed to the fact that only Athlon XP's benefit from the optimizations in that kernel.


So basically, I recommend that you use an i686 kernel.[/QUOTE]

---

