---
title: "Physical  XP on SATA in VMWare?"
date: 2006-09-08
forum: General Help
---

### Post by refactored on 2006-09-08
Hi

Is it possible to run a physical installation of XP through VMWare when the installation resides on a SATA disc (NTFS partition)? I keep getting the BSOD without any good information when booting it up.

/refactored

---

### Post by rbmorse on 2006-09-08
Does the host machine have write access to the NTFS partition?  THe VM can't do anything the host can't.

---

### Post by rbprogrammer on 2006-09-08
i was wondering about that too.  b/c i have windows xp on another partition and i want to acess it through vmware.  b/c when i install windows on vmware, the activation codes never work.  as of now i dont have write capabilities for the ntfs partition, but i might think about getting that package that allows me to "safely" write to ntfs (i know it is still experimental").

assuming i have write access to the ntfs partition, how would i go about using that physical windows installation through vmware?

---

### Post by refactored on 2006-09-08
Well, now I've spent a couple of hours converting the NTFS partition into FAT32 and ensuring that it is indeed writeable for the host. But I keep getting that blue screen so I guess VMWare still has issues with SATA drives?

They do state that running physical installations on SATA is unsupported. But unsupported does not mean that it won't work.

Anyone who knows how to debug this issue?

/refactored

---

