---
title: "Installation Errror"
date: 2006-12-04
forum: General Help
---

### Post by SDX on 2006-12-04
Hi! Everytime I try to install Ubuntu, it says "Loading Linux Kernel", and then displays this:

UNKNOWN INTERRUPT OR FAULT AT EIP 000000 C01002B1 00002B0
UNKNOWN INTERRUPT OR FAULT AT EIP 000000 C01002B1 00002B0
UNKNOWN INTERRUPT OR FAULT AT EIP 000000 C01002B1 00002B0
UNKNOWN INTERRUPT OR FAULT AT EIP 000000 C01002B1 00002B0
UNKNOWN INTERRUPT OR FAULT AT EIP 000000 C01002B1 00002B0
UNKNOWN INTERRUPT OR FAULT AT EIP 000000 C01002B1 00002B0
UNKNOWN INTERRUPT OR FAULT AT EIP 000000 C01002B1 00002B0
UNKNOWN INTERRUPT OR FAULT AT EIP 000000 C01002B1 00002B0
UNKNOWN INTERRUPT OR FAULT AT EIP 000000 C01002B1 00002B0
UNKNOWN INTERRUPT OR FAULT AT EIP 000000 C01002B1 00002B0

Then, my computer reboots. I've tried all kinds of stuff, but this error keeps on happening. Does anybody know how to fix this?

---

### Post by renzokuken on 2006-12-04
post your hardware specs.

laptop or desktop?

---

### Post by man_of_the_bush on 2006-12-18
I get exactly the same error. I have a desktop:
Compaq Presario Pentium 4 2.8GHz with 512MB ram

---

### Post by hayabusa on 2006-12-21
There is probably a processor type mismatch of some sort.  I ran into this installing 6.10 in a Parallels virtual machine, and I think there's also an issue with [vmware]("www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=2020").  There are issues with 6.10 and processors that do not support [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension"), including processors in virtual machines.  I got around my issue by installing 6.06.1.

I'm not sure how to turn off pae, if this is indeed your issue.  If anyone knows how, please post!

---

### Post by ekasad on 2007-01-03
Yes, I also have this problem with a Compaq Presario, which is probably also the system that the original poster has as well.

> FAULT AT EIP 00000000 c01002b1 000002b0

This system is notorious for not working well with any linux. I have tried various other live CD distros before such as knoppix or slax, with various errors resulting in a failed boot each time.

Let it be known: The Compaq Presario SR1000V is a HORRIBLE machine hellbent on solely booting Windows.

If ANYONE can offer salvation to its damned users please speak up and help. ](*,)

---

### Post by ekasad on 2007-01-04
Alright, I have a solution. :) 

By pressing F6 at the Ubuntu boot screen and using the boot parameter acpi=off I was able to use a session with gnome just fine.

---

