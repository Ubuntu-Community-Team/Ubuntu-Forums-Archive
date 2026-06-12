---
title: "simultaneous connection limit in linux?"
date: 2007-01-04
forum: General Help
---

### Post by teknoPunk on 2007-01-04
In windows XP SP2 I know there is a 10 simultaneous connection attempt limit (although I applied the Evl patch and so no have a much higher cap).  I am configuring azureus and am wondering if there is a similar limit in ubuntu/linux?

Thanks!

---

### Post by az on 2007-01-04
AFAIK, no.

---

### Post by Lord Illidan on 2007-01-04
Definitely not.

---

### Post by az on 2007-01-04
Does anyone know what the maximum number of tcp/ip connections that a box can have simultaneously?  For example, if there is too high a number (thousands) can that crash your box, and if so, is there some sort of limit built-into the kernel?

I know there is not some cap on the number in the same way that windows does it (just a few "allowed'" in the home edition and more "allowed" in the pro edition), but there must be some sort of OS-independant maximum?

---

### Post by fragos on 2007-01-04
MS differences between home and pro for concurrent tcp/ip connections is artificial.  Ways to get someone to pay more for the same thing.  There are probably many variables that impact how many can be handled.  For example, bandwidth, CPU power and memory size.  In practice I've never run accross problems in this area.  The number of FTP connections allowed frequently has a softwaare or configuration imposed limit.

---

