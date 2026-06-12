---
title: "qemu segfault"
date: 2005-03-22
forum: General Help
---

### Post by yanik on 2005-03-22
Hi,

I have tried to install FreeBSD, WinXP and FC3 under qemu without any success.  In all OS, qemu would segfault at about half of the install.  Used to work just fine under debian testing.  What's wrong with qemu in ubuntu?

For me this is a big show stopper...

Any suggestions? beside going back to debian testing?

Thanks

Yanik

---

### Post by WillCooke on 2005-03-22
[QUOTE=yanik]Hi,

I have tried to install FreeBSD, WinXP and FC3 under qemu without any success.  In all OS, qemu would segfault at about half of the install.  Used to work just fine under debian testing.  What's wrong with qemu in ubuntu?

For me this is a big show stopper...

Any suggestions? beside going back to debian testing?

Thanks

Yanik[/QUOTE]
 I'm having similar problems.  Win98 installed ok, then started  seg-faulting qemu, and W2k wouldn't even install.

I've given up and found an old P233 to use instead.

---

### Post by yanik on 2005-03-23
I just want to say I tried replacing vgabios, bochsbios and qemu with the ones from debian testing and it still seg faults.  

So I guess this must be a kernel issue?  What would happen if I get my kernel off debian unstable?

Anyway, I' back on debian testing for now, I'll come back when hoary final comes out  and see if qemu is fixed.

Thanks

Yanik

---

