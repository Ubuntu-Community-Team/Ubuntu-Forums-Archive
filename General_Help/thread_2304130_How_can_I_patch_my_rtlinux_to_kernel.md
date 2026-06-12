---
title: "How can I patch my rtlinux to kernel?"
date: 2015-11-24
forum: General Help
---

### Post by latha2 on 2015-11-24
Dear all,
 Could you please help me out in patching of rtlinux to ubuntu 14.04.

---

### Post by Bucky Ball on 2015-11-24
*Thread moved to **General Help**.*

Welcome. Could you give a little more detail, please? :)

---

### Post by matt_symes on 2015-11-24
Hi

rtlinux ? real time kernel ?

You may want to look at the low latency kernels in the repositories.

```
matthew-laptop:/home/matthew:2 % acse linux-image-lowlatency
linux-image-lowlatency - lowlatency Linux kernel image
linux-image-lowlatency-pae - Transitional package
linux-image-lowlatency-lts-utopic - lowlatency Linux kernel image
linux-image-lowlatency-lts-vivid - lowlatency Linux kernel image
linux-image-lowlatency-lts-wily - lowlatency Linux kernel image
matthew-laptop:/home/matthew:2 % 

```

Kind regards

---

### Post by latha2 on 2015-11-26
Sir,I'm getting RTLinux installation steps for ubuntu 12.02 which are not working while Installating  on ubuntu 14.04 LTS  ( I'm navie to linux ). Please help me out. 
Thank you !

---

### Post by Bucky Ball on 2015-11-26
> **latha2 said:**
> Sir,I'm getting RTLinux installation steps for ubuntu 12.02 which are not working while Installating  on ubuntu 14.04 LTS  ( I'm navie to linux ). Please help me out. 
Thank you !

Perhaps because they're for 12.04 (there was no 12.02). Please read matt_syme's post again. Open Software Centrer> do a search for low latency kernel. That is the equivalent to the RT (which I'm not sure is used now).

---

### Post by latha2 on 2015-11-26
Yes,sorry sir for that mistake . Thank you !

---

