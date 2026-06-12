---
title: "implicit function in ubuntu 16.04"
date: 2018-02-08
forum: General Help
---

### Post by yzzhsx1234 on 2018-02-08
Hello, everyone

Recently, I am trying to use a kernel driver through Ubuntu, but when I type the commad "make", it shows the following error:(:

Error:implicit declaration of function 'pci_enabe_msix'
         rc = pci_enable_msix(pdev, lro->entry, req_nvec).

However, the error didn't show up when I ran the "make" in ubuntu 14.04:confused:

Can anyone can help me with that? Thank you! Also, I am a guy who just start to use the Ubuntu Linux, so please don't be angry if the questions I asked are stupid.

Thank you again!!:)

---

### Post by cruzer001 on 2018-02-08
Have you installed "autoconf" and "build-essential"?

---

### Post by yzzhsx1234 on 2018-02-08
Yes, I did install both of them

---

### Post by yzzhsx1234 on 2018-02-08
By the way, I was running Ubuntu through virtualbox, is this the possibility of causing that?

---

### Post by steeldriver on 2018-02-08
What driver are you trying to install exactly, and what is your kernel version (as indicated by `uname -r`)?

Often these kinds of issues are because of a mismatch between the two

---

### Post by cruzer001 on 2018-02-08
It looks like 'pci_enabe_msix' has been dropped in the newer kernels.

[http://dpdk.org/ml/archives/dev/2017-May/065216.html](http://dpdk.org/ml/archives/dev/2017-May/065216.html)

---

### Post by yzzhsx1234 on 2018-02-08
It is 4.13.0 -32-generic

---

### Post by yzzhsx1234 on 2018-02-08
so which means I may have to replace it with other function can work in the same way ?

---

### Post by cruzer001 on 2018-02-08
The above link suggest using 'pci_enable_msix_range'.

Will it work in the same way?  I have no way of knowing.

---

### Post by yzzhsx1234 on 2018-02-08
It looks work, since I have switch "pci_enable_msix()" to "pci_enable_msix_range_()", the error is different :

Error: too few arguments to function 'pci_enable_msix_range'
rc = pci_enable_msix_range(pdev, lro->entry, req_nvec)

---

### Post by cruzer001 on 2018-02-08
The 4.4 kernel is supported till 2021 in 16.04 and still has "pci_enable_msix".

---

### Post by yzzhsx1234 on 2018-02-09
I have tried the "pci_enable_msix_range()" and it worked, but it may need to make a little change about arguments

---

