---
title: "What is this error ?"
date: 2008-06-08
forum: General Help
---

### Post by Davi0 on 2008-06-08
And how do I correct it so I can achieve install of Hardy.

When install from live cd reaches partitioner, partitioner loads then I get what presume is an error message. This in the form of a small box with a picture of a hard drive and heaps of ?????? marks. The only option on this box is "OK" and when I hit this button the install falls back to the language selection stage. If I hit "forward" then the install just sits there "busy" sign endlessly active.

I suspect Hardy can't see the hard drive which is an IDE drive in a removable rack. The only other drive in this machine is a data drive on SATA 1.

I have prepared the drive I am trying to install on with GParted by removing all partitions and 1st I tried leaving all space unallocated, then I formatted the whole disk as 1 ext2.

Any suggestions

---

### Post by bingoUV on 2008-06-08
1. Which language did you select?
2. Try installing in text mode. It is not as bad as it sounds. It is also a UI, just less shiny than the graphical installer.

---

### Post by Davi0 on 2008-06-08
Language - US

Presume I press F4 at install selection to obtain text mode ?

---

### Post by bingoUV on 2008-06-08
In my Ubuntu Live CD, the options while booting were
1. Live/Install graphical
2. Text mode

If it is so with you, choose the second option.

---

