---
title: "minimal lubuntu missing eth0"
date: 2014-11-04
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-11-04
i installed via the mini.iso image
at the time the HDD was in my main rig with this NIC, this was temporary as i was doing the install for another system but i did not want to wait on the hardware to arrive for it
05:00.0 Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 10)
i have tried booting it on several other systems, i cant get a Ethernet connection working
i thought the driver was in the kernel for these, but that seems to not be the case as i am using the mainline 3.16.6 lowlatency kernel
is there a particular package with the common NIC drivers in it? one i can download onto a usb and install via dpkg

---

### Post by sudodus on 2014-11-05
The default installation from mini.iso is a network, that is not portable (which is different from that of the Lubuntu iso files). But you can make it portable with the tweaks of this wiki page

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)

This is the method I used for the OBI-9w system described at

[https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w)

---

### Post by pqwoerituytrueiwoq on 2014-11-08
thanks, installing network-manager got what i needed
a bit of a pita downloading about 12-18 debs to install it though (you know cause i needed that to use the NIC to download packages)

---

### Post by sudodus on 2014-11-08
Yes I know.

---

