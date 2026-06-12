---
title: "Outgoing IP Packages"
date: 2008-05-03
forum: General Help
---

### Post by eldoctor on 2008-05-03
Hi this is my first post here!! Great forum btw, lots of information!!
Well the problem is this:

I want to know the amount of Outgoing IP Packages on my PC and the processes with outgoing sockets (not connected to localhost), is there any command to do this?? or any file in the /proc directory that would help??

Thanks!!

---

### Post by Monicker on 2008-05-03
To see established connections with external hosts

```
sudo netstat -anltp |grep ESTABLISHED
```


For outgoing packets you can get a general idea by looking at the interfaces
```

ifconfig
```

...and then looking at the number of tranmitted packets.


If you want something more precise you could use an iptables rule to log outbound packets, and then check it with "sudo iptables -v -L".


How much detail are you wanting exactly?  Are you looking to keep a historical record?

---

### Post by eldoctor on 2008-05-04
Thanks for the answer, I need this for a project at University, I created a shell that has a module that needs to check the amount of inet traffic. The netstat command works great :D, what part of the ifconfig output should I cut out for the amount of outgoing IP packages??


wlan0     Link encap:Ethernet  HWaddr 00:18:f8:b0:56:93  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f8ff:feb0:5693/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10280598 (9.8 MB)  TX bytes:2984924 (2.8 MB)

Thanks

PS: I created by mistake a copy of this thread in "Absolute Beginner Talk", if the admins want to delete it its OK.

---

### Post by ghost_ryder35 on 2008-05-04
TX packets:12804 errors:0 dropped:0 overruns:0 carrier:0

---

### Post by eldoctor on 2008-05-04
Works great! My other team member also found this way of getting the outgoing IP packages:

cat "/proc/net/dev" | grep "wlan0" | awk '{print $10}'

Thanks for the info!!

---

### Post by eldoctor on 2008-05-04
I have a problem... which is the socketID in the ootput of "sudo netstat -anltp |grep ESTABLISHED"??

Bye

---

