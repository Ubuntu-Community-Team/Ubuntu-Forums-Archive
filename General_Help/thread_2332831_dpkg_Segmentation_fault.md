---
title: "dpkg Segmentation fault"
date: 2016-08-04
forum: General Help
---

### Post by steve-gnusys on 2016-08-04
dpkg produces a Segmentation fault with any or no parameters on a production server ( 14.04.04 LTS) which I only have ssh access to.

I assume the binary is corrupted. I tried overwriting /usr/bin/dpkg with copies retrieved from another server running the same version of Ubuntu but get
"cannot execute binary file: Exec format error"

Grateful for any advice on how to recover this.

Steve

---

### Post by steve-gnusys on 2016-08-05
Rebooted machine after 168 days, after a few cycles it finally booted with no fs errors.  

But dpkg still segfaults.  I realise the architecture is i686 on this machine, which explains the "Exec format error" when trying to run dpkg copied from other servers which are x86_64.  

I'm having trouble finding dpkg for i686  to attempt to repair this problem. If anyone has any pointers that would be great.

---

### Post by steve-gnusys on 2016-08-05
OK.  I obtained i386 version from 

[http://packages.ubuntu.com/trusty/i386/dpkg/download](http://packages.ubuntu.com/trusty/i386/dpkg/download)

and unpacked it on a working machine to obtain a copy of the dpkg binary with
dpkg -x 

After copying the extracted dpkg to the affected server I have been able to update and upgrade normally.

---

### Post by oldos2er on 2016-08-05
Hello, would you please mark your thread 'Solved' under Thread Tools at the top of the page? Thank you, and I'm glad your problem is fixed.

---

