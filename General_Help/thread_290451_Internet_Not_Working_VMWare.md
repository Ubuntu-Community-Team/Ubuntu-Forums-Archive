---
title: "Internet Not Working VMWare"
date: 2006-11-01
forum: General Help
---

### Post by OffHand on 2006-11-01
Hi there,
I installed VMWare server on my Edgy machine.
Downloaded the Dapper virtual appliance and I am able to boot it.
Once booted I do not have a working internet connection though.
Can anyone help me troubleshoot this issue please?
Thanks in advance,
OffHand

---

### Post by OffHand on 2006-11-01
It's working!
What I did was enable internet connection sharing with Firestarter on device vmnet8. Then in VMWare server I picked custom device and told it to use /dev/vmnet8
After that it worked.

---

### Post by Jeremy Jackins on 2008-02-12
Thanks for posting you solution, this helped me alot!

---

