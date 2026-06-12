---
title: "[SERVER] Boot Problem - NC6000"
date: 2007-06-01
forum: General Help
---

### Post by FPSTom on 2007-06-01
Hello,

Just installed Ubuntu Server 7.04 on my HP Compaq NC6000 Laptop. But when it boots I get:

```
Int 14: CR2 c1000000  err 00000002  EIP c03f3c3e  CS 00000060  flags 00010006
Stack: 373c0046  00000000 ffffffff c0490000 00001800 00000080 00800000 ffffff80
```

Whats the solution?

Thanks
Tom

---

### Post by ve9gfi on 2007-07-24
Hi Tom,

I have the exact same error with a Compaq nc6000, running VMware on Windows XP, and Ubuntu 7.04 as the guest OS.  In fact, I get the same error with Ubuntu 6.06 too.  

I have other XPs, FreeBSD, and OpenBSD running fine in this VMWare.  My version of VMWare was 1.0.1, but I upgraded it yesterday to 1.0.3 to see if that you fix the issue, but it didn't.

Since you get this same error by running Ubuntu 7.04 natively on the hardware, then I am guessing the VMware is simply passing the Ubuntu commands to the hardware, and this error that I'm seeing is tied to the Compaq NC6000 laptop.

I'm wondering if you found a solution to get Ubuntu running on your NC6000.

Greg

---

