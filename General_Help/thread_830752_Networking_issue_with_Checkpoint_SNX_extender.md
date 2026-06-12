---
title: "Networking issue with Checkpoint SNX extender"
date: 2008-06-16
forum: General Help
---

### Post by eddy_crim on 2008-06-16
I have set up the SNX checkpoint extender according to the discussion here
[http://ubuntuforums.org/archive/index.php/t-444166.html](http://ubuntuforums.org/archive/index.php/t-444166.html)

It works great but i seem to have a routing problem that im not sure how to fix, (my networking knowledge is a bit rusty)

When i connect with the above the tunsnx adapter is given an ip on the 192.168.13.* subnet, this allows me to then connect to the 192.168.10.* subnet on which most of the companies servers/systems reside. However my company has another office with a 192.168.40.* subnet which i am **not** able to connect to. 

I think the problem here is a simple routing one because *if* i connect using checkpoints (nasty) windows client i am still assigned a 192.168.13 address and can access 192.168.40.* address fine.

I have posted my route table in the hope that it will help decipher what is going on. Any help would be appreciated

Ed

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.13.18   *               255.255.255.255 UH    0      0        0 tunsnx
172.250.250.1   *               255.255.255.255 UH    0      0        0 tunsnx
172.250.250.2   *               255.255.255.255 UH    0      0        0 tunsnx
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
195.157.50.11   *               255.255.255.255 UH    0      0        0 tunsnx
192.168.130.113 *               255.255.255.255 UH    0      0        0 tunsnx
test.ip.dircon. *               255.255.255.255 UH    0      0        0 tunsnx
192.168.127.1   *               255.255.255.255 UH    0      0        0 tunsnx
www.cardinal.co *               255.255.255.255 UH    0      0        0 tunsnx
192.168.130.114 *               255.255.255.254 U     0      0        0 tunsnx
195.157.50.224  *               255.255.255.254 U     0      0        0 tunsnx
192.168.127.2   *               255.255.255.254 U     0      0        0 tunsnx
192.168.130.48  *               255.255.255.240 U     0      0        0 tunsnx
192.168.129.144 *               255.255.255.240 U     0      0        0 tunsnx
192.168.130.144 *               255.255.255.240 U     0      0        0 tunsnx
192.168.129.176 *               255.255.255.240 U     0      0        0 tunsnx
192.168.130.176 *               255.255.255.240 U     0      0        0 tunsnx
192.168.129.208 *               255.255.255.240 U     0      0        0 tunsnx
192.168.129.32  *               255.255.255.224 U     0      0        0 tunsnx
192.168.129.96  *               255.255.255.224 U     0      0        0 tunsnx
192.168.130.0   *               255.255.255.224 U     0      0        0 tunsnx
192.168.69.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.128.0   *               255.255.255.0   U     0      0        0 tunsnx
192.168.19.0    *               255.255.255.0   U     0      0        0 tunsnx
10.48.1.0       *               255.255.255.0   U     0      0        0 tunsnx
172.16.10.0     *               255.255.255.0   U     0      0        0 tunsnx
192.168.10.0    *               255.255.255.0   U     0      0        0 tunsnx
192.168.26.0    *               255.255.255.0   U     0      0        0 vmnet1
default         *               0.0.0.0         U     0      0        0 ppp0
ed@ed-laptop:~$ 

```

---

### Post by ritchie on 2011-08-09
i am having the same Problem, did you find a solution?

---

