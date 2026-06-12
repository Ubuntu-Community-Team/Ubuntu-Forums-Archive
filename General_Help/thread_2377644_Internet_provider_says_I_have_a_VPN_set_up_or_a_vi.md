---
title: "Internet provider says I have a VPN set up or a virus."
date: 2017-11-15
forum: General Help
---

### Post by estes53 on 2017-11-15
Sites cannot identify my location.
Internet provider says I have a VPN set up or a virus.
Just installed this so seems unlikely.
Anything else I should check.

Thanx, Alan

---

### Post by QIII on 2017-11-15
Hello!

You have given us precious little to go on here.

When does this happen?  What are you doing at the time?  What applications are you using?

Our ability to help is directly proportional to the amount of information we have.

Cheers!

---

### Post by estes53 on 2017-11-15
I am using Chrome and it always happens.

---

### Post by QIII on 2017-11-15
Can you give us a more definitive description of the exact behavior you are observing?

---

### Post by estes53 on 2017-11-15
The websites have no idea what town I live in and when I tell them, the information is not saved.

---

### Post by TheFu on 2017-11-15
proxy?
route -n?

---

### Post by estes53 on 2017-11-15
Not sure what I am looking at-
echo $HTTP_PROXY
direct://
sudo route-n
direct://

---

### Post by TheFu on 2017-11-16
Those are not things to be entered into a chrome browser - though chrome does probably have a GUI where you can setup a proxy.  I don't use chrome.  Checking if a proxy is being used would entail checking chrome settings and checking the OS settings. There might or might not be an environment variable used. IDK.

Also, no need to use sudo for the route command. 'route' is something to be entered into a terminal.  
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.22.22.1     0.0.0.0         UG    0      0        0 br0
172.22.22.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
```
is mine, without a VPN running.  With a VPN, it looks like this:
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.16.10.9      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         172.22.22.1     0.0.0.0         UG    0      0        0 br0
10.16.10.1      10.16.10.9      255.255.255.255 UGH   0      0        0 tun0
10.16.10.9      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
104.238.169.91  172.22.22.1     255.255.255.255 UGH   0      0        0 br0
128.0.0.0       10.16.10.9      128.0.0.0       UG    0      0        0 tun0
172.22.22.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
```
See how more complex it is?

---

