---
title: "Samba with Multiple NIC's"
date: 2013-11-13
forum: General Help
---

### Post by weird0.kid on 2013-11-13
Hi

I have an old server i want to use for various network shares.  The server has 3 NIC's.
I want to configure samba in such away that when i connect to a share on eth1's ip address and transfer data, it is carried over eth1.  

Currently, even if i connect to the ip address of eth1 when the transfer is started, the data is moved via eth0.
In the samba config i have specified:

interfaces = eth1 192.168.0.254
bind interfaces only = yes

But this doesn't provide the desired affect.

Any advice / help would be greatly appreciated

---

### Post by TheFu on 2013-11-13
Are your NICs on the same subnet?
What does the routing table look like?

Look into bonding your NICs into a single virtual NIC ... of course, you will need enterprise network equipment or this doesn't work at all.  The switch must support bonded connections, you'll need to correctly, manually, configure the /etc/network/interfaces file for bonding. I think the kernel driver is there already, but check that too.

Does that make sense?

If bonding is NOT what you want, then you'll need to setup specific routes between the IPs involved. At least that would be my method. I suspect your network stack is using the default route ... because that is almost always what people want. To do anything else, extra effort is needed.

---

### Post by weird0.kid on 2013-11-13
Yes the nics are all on the same range:
eth0:  192.168.0.254
eth1:  192.168.0.229
eth2:  192.168.0.228

Routing Table:
root@backup:/home/weirdo# netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2
192.168.3.0     192.168.0.1     255.255.255.0   UG        0 0          0 eth0
192.168.4.0     192.168.0.1     255.255.255.0   UG        0 0          0 eth0
192.168.5.0     192.168.0.1     255.255.255.0   UG        0 0          0 eth0
192.168.6.0     192.168.0.1     255.255.255.0   UG        0 0          0 eth0
192.168.7.0     192.168.0.1     255.255.255.0   UG        0 0          0 eth0
root@backup:/home/weirdo#

All 3 the nics plug into a Layer3 switch, and would support a NIC bonding type of setup.  
But is my problem not Samba related?

---

### Post by TheFu on 2013-11-13
> **weird0.kid said:**
> Yes the nics are all on the same range:
eth0:  192.168.0.254
eth1:  192.168.0.229
eth2:  192.168.0.228

All 3 the nics plug into a Layer3 switch, and would support a NIC bonding type of setup.  
But is my problem not Samba related?

The output from **route** would be helpful. Need to see the metrics for each interface.
Having 3 default routes ... odd.

IMO, this is NOT a samba issue. Samba sits on top of the network stack. Expecting it to override it ... well, I wouldn't.

---

### Post by weird0.kid on 2013-11-13
root@backup:/home/weirdo# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth2
192.168.3.0     192.168.0.1     255.255.255.0   UG    0      0        0 eth0
192.168.4.0     192.168.0.1     255.255.255.0   UG    0      0        0 eth0
192.168.5.0     192.168.0.1     255.255.255.0   UG    0      0        0 eth0
192.168.6.0     192.168.0.1     255.255.255.0   UG    0      0        0 eth0
192.168.7.0     192.168.0.1     255.255.255.0   UG    0      0        0 eth0
root@backup:/home/weirdo#

---

### Post by TheFu on 2013-11-13
It would be helpful if you wrapped output in "code" tags, please. So columns line up.

Having 3 default routes all with the same metric ... what is the defined behavior for that?  I wouldn't know. Plus, it seems that eth0 is the primary-default ... so outbound traffic would go over that interface unless special routes were created with a lower metric.  From the table above, seems all metrics are (0) ... so you can't make any special route a lower priority.

How is your networking knowledge?

---

### Post by SeijiSensei on 2013-11-13
You'll find life much easier if each interface is on a separate subnet.  Otherwise you'll have a variety of routing problems.

---

### Post by weird0.kid on 2013-11-15
I installed FreeNAS and all my problems have since been resolved.

---

### Post by TheFu on 2013-11-15
> **weird0.kid said:**
> I installed FreeNAS and all my problems have since been resolved.

The network setup under freeNAS will have the same issues, if configured in the same way.  Could you please post the output from the same commands previously requested?  I'd like to learn.

---

### Post by weird0.kid on 2013-11-18
On FreeNAS i was able to setup Link Aggregation, and it gave me 1ip address.  the system is spreading the load nicely between the 3 NIC's

---

