---
title: "System monitor vs top re RAM usage"
date: 2005-03-20
forum: General Help
---

### Post by bogl on 2005-03-20
I am baffled.

The System Monitor give a different, lower figure for RAM usage than top.

Eg at the moment, S.M. says I am using 325Mb of 727Mb.

top, however, gives 

743984k total,   705740k used

Why might I have this discrepancy?

bogl

---

### Post by Juergen on 2005-03-21
The just have different ways to show used memory.

To get similar values, take the 'used' from top, and subtract 'buffers' and 'cached'

If your apps don't use all memory, Linux takes it as disk-cache - and top shows the total, SM only the apps.

---

### Post by bogl on 2005-03-21
Thanks for that explanation Juergen.  I was beginning to think it was something like that, but you've made it very clear.

---

