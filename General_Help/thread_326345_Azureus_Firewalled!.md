---
title: "Azureus Firewalled!?"
date: 2006-12-27
forum: General Help
---

### Post by olieviya on 2006-12-27
My Azureus was setup and running smoothly yesterday night/today morning, but now it has decided it's firewalled.:confused: 
I cannot think of what i am doing wrong, :-k  I have been using Azureus for a while now and I know my settings are correct, i just checked them again anyway on the wiki to make 100% sure.
I am using a good port and it's forwarded using the gateway I'm behind, and the port is open in my firewall.
Why is it saying firewalled then?

](*,) ](*,) ](*,) ](*,)  

```
My iptables:
 sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:51112 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:51112 flags:SYN,RST,ACK/SYN state NEW 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     
```

 Ask me if I've left some info behind you may need.

Thanks in advance.

---

### Post by olieviya on 2006-12-27
anybody help?:-?

---

### Post by hanzomon4 on 2006-12-27
My does this from time to time, Check to see if the nat test still works. If it does the firewall thing will eventually go away

---

### Post by LenzM on 2006-12-27
I've had this happen once and it went away when I restarted the networking

```

sudo /etc/init.d/networking restart

```

---

### Post by olieviya on 2006-12-28
> **LenzM said:**
> I've had this happen once and it went away when I restarted the networking

```

sudo /etc/init.d/networking restart

```

I dunno if this is all relevant but here is what I got:
```

 sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3372
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:30:1b:1e:a3:35
Sending on   LPF/eth0/00:30:1b:1e:a3:35
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:30:1b:1e:a3:35
Sending on   LPF/eth0/00:30:1b:1e:a3:35
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.70 -- renewal in 21592 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]
```



> **hanzomon4 said:**
> My does this from time to time, Check to see if the nat test still works. If it does the firewall thing will eventually go away
I don't think the nat test ever worked for me...



Still firewalled :(

---

### Post by olieviya on 2006-12-29
bump

---

### Post by olieviya on 2006-12-30
Is this just going to stay a mystery? :(

---

### Post by dedmonds on 2007-03-26
bump (I'm having the same problem.)

---

### Post by garymc1 on 2007-03-30
i am having the same problem it tells me that i am firewalled the ports are open on my router as i have enabled DMZ for my ip but it still tells me i am firewalled,  any ideas ??? thanks gary

---

### Post by Catsworth on 2007-03-30
I get the same problems every now and then.

Most of the time Az works just fine, then it all goes to cock and starts failing the NAT test etc.

There's an option in the connection settions with Az to bind it to a specific IP address, if you're behind a router you might want to try changing that to the current IP address of your machine.

Also note that if your router is dynamically assigning IP addresses then your port forwarding will all go to cock each time your IP address is changed.

---

