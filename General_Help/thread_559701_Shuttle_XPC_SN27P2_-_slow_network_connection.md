---
title: "Shuttle XPC SN27P2 - slow network connection"
date: 2007-09-25
forum: General Help
---

### Post by Mithrilhall on 2007-09-25
I'm having trouble with my network connection. I've turned off the onboard NIC [Marvell 88E1116(10/100/1000Mbps)] and installed a Intel Dual-NIC.

The NIC was detected fine (as was the onboard) but when I go to browse the internet I get speeds slower than dial-up.

More information below:

AMD Athlon 5600 X2 (AM2 socket)
NVIDIA nForce 570 Ultra

[http://www.newegg.com/Product/Product.asp?Item=N82E16856101004](http://www.newegg.com/Product/Product.asp?Item=N82E16856101004)

Any suggestions on what to try next? This is driving me nuts :confused: :confused: :confused:

---

### Post by lavajumper on 2007-09-25
Slow networks suck.

Could you post a little more information? Your routing table (route -n) and the output from ifconfig would be the place to start. Another place to look is in the output from lsmod (are the modules for the new card getting loaded correctly?) Is your DNS resolving in a timely manner(less /etc/resolv.conf & dig <someinternet.address>)?

---

### Post by moe_syzlak on 2007-11-29
to all the noobs out there when ur posting problems tell us the syptoms that u are having. it will help us better

---

### Post by Mithrilhall on 2007-11-30
Moe...I'm not sure who you're calling a n00b but you might want to check the date of a post before you reply.

---

