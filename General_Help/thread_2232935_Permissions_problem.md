---
title: "Permissions problem"
date: 2014-07-05
forum: General Help
---

### Post by M1k4 on 2014-07-05
I want to modify my file [B]proc/sys/net/ipv4/ip_forward

[/B]at moment, the file countains one only character : "0"
and I would like to change it to "1"

But when I try to... I am not allowed : not enough rights
I tried with sudo but it didn't work
(I typed** sudo [B]echo 1 > /proc/sys/net/ipv4/ip_forward**[/B])

still not enough rights

can you help me please?
I am just following this [http://www.securitykiss.com/resources/tutorials/conf_linux_nm/ubuntu/](http://www.securitykiss.com/resources/tutorials/conf_linux_nm/ubuntu/)

---

### Post by M1k4 on 2014-07-05
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

solution from [http://forum.ubuntu-fr.org/viewtopic.php?id=32564](http://forum.ubuntu-fr.org/viewtopic.php?id=32564)

---

