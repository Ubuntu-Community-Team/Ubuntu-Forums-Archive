---
title: "Single VGA passthrough"
date: 2021-10-05
forum: General Help
---

### Post by ataulmarcia on 2021-10-05
I'm trying to configure single VGA passthrough for my graphics card, but I can't load the vfio_pci driver using modprobe.
Which can be the cause?
I use Nvidia GT 1030, ubuntu 20.04, and kernel 5.10

---

### Post by monkeybrain20122 on 2021-10-06
I think this is about virtualization and should go to the virtualization subforum and you should give more details about your set up and what steps are you trying to follow. I don't know anything about VGA passthrough except that you normally need two GPUs. There are blog posts and tutorials about single GPU passthrough but seems very risky based on feedbacks. Many people reported bricked machines as a result.

---

### Post by ajgreeny on 2021-10-06
If this is a VM, what is the host, what is the guest, and whicn virtualisation application are you running it on, Virtualbox, KVM/QEMU or something else?

---

