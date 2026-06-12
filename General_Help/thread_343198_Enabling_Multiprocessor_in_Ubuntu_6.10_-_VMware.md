---
title: "Enabling Multiprocessor in Ubuntu 6.10 - VMware"
date: 2007-01-21
forum: General Help
---

### Post by pikachu01 on 2007-01-21
I'm using VMware to run Ubuntu 6.10

cat /proc/cpuinfo just shows

processor:                     1

whereby I have two processors and turned number of virtual processors in VMware to two(2).

---

### Post by kuja on 2007-01-21
I'm assuming vmware server, in which case it would be done like this, go to that virtual machine -> edit virtual machine settings. Go down to processors and change the number from one to two, and you should be golden.

---

### Post by rianquinn on 2007-01-21
Don't forget that the default Kernel for Ubuntu doesn't support SMP. you need to install the linux-686-smp package to get SMP working. You might also have to unlock the universe and multiverse repos to get the package

---

