---
title: "Installing Dapper kernel source/headers"
date: 2006-07-07
forum: General Help
---

### Post by AZzKikR on 2006-07-07
For some NForce4 driver i need to install the kernel source and its headers alongside build-essential.

Now, when I use Synaptic to look up the kernel source, it only gives an entry for kernel 2.4, whereas I am using 2.6.15-25-386 (returned by `uname -r`).

How would I install the headers and source for my kernel version? I'm on Dapper Drake.

---

### Post by hegenious on 2006-07-07
in ubuntu the kernel-headers are called linux-headers.
do a search for it in synaptic after you have added all repositories (also in synaptic).

---

### Post by AZzKikR on 2006-07-07
Thanks! You were my last step into making my 4 speakers work!

$ sudo apt-get install linux-headers-`uname -r`

did the trick!

---

