---
title: "2 Ubuntu Machines can't ping or ssh each other"
date: 2008-05-08
forum: General Help
---

### Post by kinghowdy on 2008-05-08
I recently bought a new computer. I took my old one filled it up with some hard drives and am I hoping to have it be a file server and maybe some other uses. 

I installed Ubuntu Hardy Server on the machine and I cannot ping, SSH or see the samba shares from my Ubuntu Hardy Desktop. I can access Apache and the torrentflux webpage I configured. However when I boot into Windows on my desktop I can access all the machine from through all protocols.

ufw is not running on either machine and it is worth mention I have one of those horrible actiontec routers model no. mi424wr.

Any help with this would be greatly appreciated!

---

### Post by Monicker on 2008-05-08
Please give the results of these commands, from both machines:

```
ifconfig
netstat -nr
```

---

### Post by kinghowdy on 2008-05-08
Thanks for the quick reply. On the server it looks like this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

and the client/laptop eth1 is the wireless it does not work even when it plugged in the thernet

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0    0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0    0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0    0 eth1

Thanks

---

### Post by Monicker on 2008-05-08
It would have been nice to have seen the ifconfig information which was requested.  I can't tell which machine has what ip address based on just the routing tables.

Are you saying that only the client has no connectivity?  Can it connect to any Internet web sites?

---

### Post by kinghowdy on 2008-05-09
I'm sorry I overlooked the ifconfig. To make a long story short I have it working now. I booted the Ubuntu Live CD and was able to SSH into the server. I knew the problem had to be with my laptop's configuration. I downloaded Firestarter and as soon as I did I was able to ssh, samba and everything else I needed. Thanks for your help.

---

