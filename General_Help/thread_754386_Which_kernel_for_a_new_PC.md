---
title: "Which kernel for a new PC"
date: 2008-04-13
forum: General Help
---

### Post by lowhat on 2008-04-13
Hi
I don't know if this is the correct forum to post this question, If it isn't, sorry for that.

Anyway, here's my question:
I'm going to purchase a new PC with an Intel Core 2 Duo E8200 and 4GB of memory, so I'm wondering which one should be the best kernel for this architecture... i386? amd64? any specific one that supports the 4GB of RAM? amd64 supports it, but my processor it's not an AMD... :S

thanks

---

### Post by sekinto on 2008-04-13
I think it is just called amd64 because AMD invented the architecture. It should work if you are using a Core 2 Duo, I'm almost positive Core 2 Duos support amd64, as well as i386, but amd64 would be a better choice.

---

### Post by forrestcupp on 2008-04-13
Before you go the 64-bit route (which will work with your computer), study it out and make sure everything you want will work with it.  I tried it in Gutsy, and certain things were a pain, so I went back to 32-bit land.

If you want to go 32-bit, you'll download the standard x86 based version and use the Generic kernel for newer computers.  the 386 kernels don't support the new features found in procs.  But the Generic kernel is going to be default in a 32-bit OS anyway.

---

