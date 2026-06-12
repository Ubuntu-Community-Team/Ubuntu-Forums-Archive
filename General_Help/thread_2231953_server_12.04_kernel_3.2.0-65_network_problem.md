---
title: "server 12.04 kernel 3.2.0-65 network problem"
date: 2014-06-29
forum: General Help
---

### Post by panotheque on 2014-06-29
old kernel good 
3.2.0-64-generic #97-Ubuntu SMP Wed Jun 4 22:04:21 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

new kernel : 3.2.0-65 => very bad network performances !
tested on 2 VM (VMWare ESXi 5.5U1) forwarding packets between 2 or more networks.

02:00.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)

back to 3.2.0-64 on the 2 VM necessary to restore performances.

Best regards

---

### Post by loewi on 2014-07-07
Same problem here.

We use the machine as firewall. With 3.2.0-65 we suffer from instable network connections (timeouts, lost connections).

Our hardware: virtual machine, ESXi 5.0, 2 network interfaces (vmxnet3):

03:00.0 Ethernet controller: VMware VMXNET3 Ethernet Controller (rev 01)
0b:00.0 Ethernet controller: VMware VMXNET3 Ethernet Controller (rev 01)

---

### Post by loewi on 2014-07-07
See also: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1337281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1337281)

---

