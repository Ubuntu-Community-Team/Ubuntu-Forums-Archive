---
title: "Network startin problem"
date: 2005-10-24
forum: General Help
---

### Post by Backo on 2005-10-24
I have a problem with my network.
Every time I log on to Ubuntu I have to activate the network device to get it started. After that everything is fine, but I hadn't this problem on 5.04. Any ideias how to "teach" ubuntu that the network should be activated on boot.
I have an integrated Intel NIC.
10x in advance.

---

### Post by tomach on 2005-10-24
try to add

ifconfig eth0 up

in

/etc/rc0.d/S35networking

should help.

---

### Post by Backo on 2005-10-25
no doesn't help
I add it in the end of the file and it didn't helkp. After I restarted the network was down again.

---

