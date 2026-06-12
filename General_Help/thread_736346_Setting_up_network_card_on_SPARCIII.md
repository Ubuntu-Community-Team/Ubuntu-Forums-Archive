---
title: "Setting up network card on SPARCIII"
date: 2008-03-26
forum: General Help
---

### Post by themish on 2008-03-26
Hi,
I just installed ubuntu7 on a sparc3 station (blade1000) and am having some trouble with internet access.  I only have terminal access as there is no X on the machine yet.  I hear that apt-get install ubuntu-desktop will do the trick for me, but I'm not able to get onto the net.  ping [www.google.com](www.google.com) only pings 10.181.24.220 not the google servers, which means that my net is all messed up.  

Im on a university network with this machine and I have a static IP that I'm supposed to set up with a set up with 2 DNS server addresses and a hostname.  
To do this I first edited /etc/network/interfaces and did 
```
iface eth0 inet static
address <staticipaddress>
netmask <MASK>
gateway <GATEWAY>
```
Then I edited /etc/resolve.conf
```
nameserver <DNS ADDRESS>
```
Then I edited /etc/hostname
```
sun1
```
Then I edited /etc/hosts and added this line under the 2 loopback lines
```
<staticipaddress> sun1.latrobe.jhu.edu sun1

```

Then in terminal,
```
sudo ifup eth0
```

Now I can ssh into the workstation from this computer, which is also on the network, but the workstation cannot ping google!! or use aptitude :(
Did I do something wrong?

---

### Post by themish on 2008-03-26
So this is what I get on the workstation with ping google.com  
```
PING jhars.nts.jhu.edu (10.181.24.220) 56(84) bytes of data.
64 bytes from 10.181.24.220: icmp_seq=1 ttl=122 time=0.680 ms
64 bytes from 10.181.24.220: icmp_seq=2 ttl=122 time=0.722 ms
64 bytes from 10.181.24.220: icmp_seq=3 ttl=122 time=0.643 ms
```

---

### Post by themish on 2008-03-26
Is it possible for me to use ssh to somehow access aptitude on the sun workstation through my working computer?

---

### Post by themish on 2008-04-03
Anyone?

---

