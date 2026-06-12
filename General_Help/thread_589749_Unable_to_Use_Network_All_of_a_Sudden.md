---
title: "Unable to Use Network All of a Sudden"
date: 2007-10-24
forum: General Help
---

### Post by 100100101 on 2007-10-24
Hi everyone!

This is my first post here and I am an absolute newb trying out Ubuntu 7.10.

I managed to get everything up and running including WINE and WMware server... all was going well until I restarted and then it was as if the network cable got unplugged. I can't use the internet or browse the local network.

The Windows XP installation in WMware can still access the internet and network so the cable and router is definitely not the problem. I restarted the router anyway just to make sure.

Please help!

Thanks in advance

---

### Post by mahousaru on 2007-10-24
Can you post the results to 

```

sudo ifconfig -a

```

---

### Post by 100100101 on 2007-10-24
Hi! Thanks for the reply.

The results are:

eth0      Link encap:Ethernet  HWaddr 00:03:47:E9:72:0A  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fee9:720a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1557485 (1.4 MB)  TX bytes:190985 (186.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:143703 (140.3 KB)  TX bytes:143703 (140.3 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.204.1  Bcast:192.168.204.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by commonlyUNIQU3 on 2007-10-24
it looks like you have an IP address on eth0...  can you ping anything external?

Try to run the command:

```
ping google.com
```

If that doesn't work, try to run the following:

```
sudo /etc/init.d/networking restart
```

...and let us know your level of success of course...

Thanks

---

### Post by 100100101 on 2007-10-24
I tried to ping google.com but it didn't work (unknwon host)then ran the 2nd command but unfortuntely the problem hasn't changed.

---

### Post by mahousaru on 2007-10-24
Can you also display

```

route

```

Do you know what is the address of your router?  How is your xp guest connecting?  Is it bridged or NAT?

I suspect it is your vmnet8.  That is squatting on what is normally the router address.  Well personally I always set my router up as the first usable address of my subnet :p

vmnet8 is normally the NAT virtual interface (think of it as a virtual switch), whilst vmnet1 is the host only one.

*EDIT*

I'm about to go to bed, but if your router is meant to be on 192.168.0.1 and if vmnet8 is meant to be on the NAT interface then I would do this to solve it.

Make sure all virtual machines are shut-down safely.

Down vmware with

```
sudo /etc/init.d/vmware stop
```

Restart your network interface with

```

sudo ifdown eth0
sudo ifup eth0

```

Make sure you now have an internet connection

**The next bit is based on vmare server as that is what i am running on my box**

If so re-configure vmware using

```

sudo vmware-config.pl

```

Errrrr I was pretty sure on my SuSE box that was vmware-server-config.pl
Oh well use what ever command which fires up all the questions about network interfaces etc.  This time let it probe for your NAT and host only interface.

Then check everything works

Good luck!

---

### Post by 100100101 on 2007-10-25
Thanks mahousaru!

That worked! I am using bridged networking for VMware so I just reran the vmware-conflig.pl file and disabled NAT.

Really happy to be online again and exploring Ubuntu!

---

