---
title: "Detected Floppy Drive?"
date: 2007-05-28
forum: General Help
---

### Post by sooqing on 2007-05-28
When I used the LiveCD, there is a long wait when booting the kernel with the message:

Buffer I/O error on device fd0, logical block 0
Buffer I/O error on device fd0, logical block 0

I do not have a floppy drive in my laptop. This problem goes away if I installed Ubuntu onto HDD. I am using the LiveCD very often and I wish there is a kernel parameter I can pass during boot time to eliminate this waiting,

I had tried 5.04, 6.04, 6.10 and this is the first time I encountered this problem.

---

### Post by smoker on 2007-05-28
just an idea, but it seems that ubuntu is getting some info somewhere (presumably the bios) that you have a floppy or similar boot device. try going into the bios setup and disabling any boot devices except cd-rom and hard drive,

hope this helps

---

