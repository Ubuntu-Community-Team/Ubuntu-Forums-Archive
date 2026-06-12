---
title: "System crashes, are they dangerous?"
date: 2006-12-26
forum: General Help
---

### Post by xsism on 2006-12-26
My system is in need of a new CPU fan.

It keeps overheating and freezing my PC. Will this adversely affect Ubuntu or any programs besides the obvious data loss of opened docs etc.

I'm especially asking about FS corruption. Am I at risk?

---

### Post by Engnome on 2006-12-26
Depends on what filesystem you are using, if you are unsure you are probably using ext3, it's a journaled filesystem so you are safer than for example fat32 or ext2. No filesystem likes crashes though, ext3 however handles them pretty well.

Checking a filesystem can be done with fsck.

---

### Post by scrooge_74 on 2006-12-26
Go get a CPU fan in a hurry, I lost the other day a PC which seems to have been overheating a little bit everyday until it just gave out. :(

---

### Post by fragos on 2006-12-26
Linux will usually recover from a crash.  Worst case some data you were working on may be lost but applications like openoffice do a recovery as well.  The real issue is the CPU which dies a little every time it overheats.  Heat is one thing that distroys semiconductors like your CPU.  Buy a new fan pronto.

---

