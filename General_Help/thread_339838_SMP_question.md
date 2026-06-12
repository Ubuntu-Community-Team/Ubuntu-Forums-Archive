---
title: "SMP question"
date: 2007-01-16
forum: General Help
---

### Post by Orion Cthulhu on 2007-01-16
I have a Pentium 4 D 805 and when I was using Dapper, dmesg would tell me that it brought up two processors. (I was using the 686-SMP kernel). Now with edgy I can't figure out how to use both processors.Dmesg keep telling me that it brought only one processor. Can someone help me? I've tried to compile a new kernel, but it didn't help.

One more thing: to actually use edgy I have to use "nolapic" as a kernel parameter, If I don't the system gets stucked at "Mounting root filesystem". After some googling I found out that one reason for this kind of problem is issues with SATA II hds. After that I tried to compile a new kernel 2.6.19 with SATA II support. After that, dmesg started to show some messages talking about SATA (those messages haven't appeared before) but I still had to use "nolapic". Can someone explain me or give me some help? 
Note: With these new kernel I still wasn't able to use both processors.

---

### Post by mcduck on 2007-01-16
Using the generic kernel (not 386) your CPU should work just fine.

---

### Post by Orion Cthulhu on 2007-01-16
> **mcduck said:**
> Using the generic kernel (not 386) your CPU should work just fine.

I am using the generic kernel and it still shows only one CPU

---

