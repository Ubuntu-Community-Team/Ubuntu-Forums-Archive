---
title: "Fixing my server's LAN ip"
date: 2007-04-03
forum: General Help
---

### Post by ykhun on 2007-04-03
I had a 6.10 server running in a LAN. There isn't any DHCP server and the router isn't able to bind MAC address to ip. Meaning it will assign ip to all the machines differently again in the event it is reboot.

My question is, how can i fixed my server's LAN ip to something like 192.168.0.99 ?

---

### Post by dfreer on 2007-04-03
Edit the /etc/networking/interfaces file.

You can specify whether to have an static IP address or one assigned by dhcp in there. Although what you probably want to do is give your server a static IP address, and then make it a DHCP server to give out IP addresses to all the computers on your LAN.

---

### Post by ykhun on 2007-04-10
Hi,

Actually, i just want my box to use a static LAN ip. That way, i can port forward on my router w/o fear that the LAN ip will change.

Anyways, i edit /etc/network/interfaces as shown below and restarted network.

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

My box now gets a static ip of 192.168.1.99. It worked for a few days, then one day i couldn't access my box. I found the following log messages:

```
Apr  9 02:52:16 xx dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Apr  9 02:52:16 xx dhclient: DHCPACK from 192.168.1.1
Apr  9 02:52:16 xx dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Apr  9 02:52:16 pong dhclient: bound to 192.168.1.107 -- renewal in 32426 seconds.
```

Some how it is trying to get an ip from the router again and binding itself to 192.168.1.107. I rebooted the box and it is back to 192.168.1.99 and the file /var/lib/dhcp3/dhclient.eth0.leases does not exist.

Any1 had any idea what is going on? I just need to make sure the box's LAN ip never change.

(note: router doesn't support ip-mac binding so that option is out of the question)

---

### Post by dfreer on 2007-04-10
hmmm. it shouldn't be using dhcp unless you specifically run sudo dhclient eth0 or have dhcp setup in your /etc/networking/interfaces file. See if it does it again, if it does you might have to look into your startup scripts/services and cron jobs to see what could be invoking it. The first time may have been a fluke.

---

### Post by ykhun on 2007-04-10
Hi thanks for the advice.

Do you know where or who could be making that dhcp request? The installation is just a basic 6.10 ubuntu server and the interfaces file is as shown in my previous post where dhcp had been commented out. I'd checked the crontab, there are no jobs in there at all.

Thanks again!

---

### Post by Austin_KW on 2007-04-10
Did you install network-manager and tell it to dhcp for eth0

---

### Post by ykhun on 2007-04-18
> **Austin_KW said:**
> Did you install network-manager and tell it to dhcp for eth0

Nope, didn't do that. It's a pretty basic setup.
A side qn: How can i check if network-manager is installed?

---

### Post by dfreer on 2007-04-18
hmmm. This should let you know if it is installed (probably not the best way to see if a program is installed, but it'll do):

```
$ whereis network-manager
network-manager: /usr/lib/network-manager
```

If it isn't installed it should look like this:

```
$ whereis network-manager
network-manager:
```

---

### Post by Austin_KW on 2007-04-18
Did you "ifdown eth0" b4 you edited the /etc/network/interfaces because it may have left the dhcp client running on eth0. Of course this presumes that you have not rebooted.

Try a "sudo killall dhclient3" and hopefully the problem will not re-occur. 

BTW, what is your router, Often the dhcp 'bind' to address is implemented by setting long lease timeout, these should be saved by the router in nvram across reboots.

---

### Post by M1GEO on 2007-08-29
Dear all.

Had exactly the same problem as was described here.  Just completely rebooted the system, "sudo reboot now" and when it rebooted, the problem was completely solved.

George Smart
M1GEO

---

