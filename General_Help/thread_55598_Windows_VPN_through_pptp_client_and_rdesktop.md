---
title: "Windows VPN through pptp client and rdesktop"
date: 2005-08-09
forum: General Help
---

### Post by salsafyren on 2005-08-09
Hi,

I am trying to connect to a Windows computer through pptp client and rdesktop once connected. I am using PPTP Client, running:

1) sudo pptpconfig. I type in the parameters necessary and start. It connects and I can ping, from pptp client.
2) rdesktop HOSTNAME

where HOSTNAME is a computer on the VPN with its domain name attached. I have tried to ping the machine (I know it is alive) but nothing happens (I cannot ping it from the command line). Rdesktop cannot connect to the computer.

It works fine in Windows. I really would want to make it work on Ubuntu.

Best regards,

Chris

---

### Post by flyinglizard on 2005-08-09
Try ping/rdesktop with the IP address instead of the hostname.

---

### Post by salsafyren on 2005-08-09
[QUOTE=flyinglizard]Try ping/rdesktop with the IP address instead of the hostname.[/QUOTE]

I tried to ping the ip adresses of the name servers and they don't answer. 

Should pptpconfig be configured more? I just gave name, server, username and password.

/Chris

---

### Post by flyinglizard on 2005-08-09
What do you have selected on the Routing tab?

For my VPNs I have the "Client to LAN" radio button selected and I add the remote network via the "Edit Network Routes" button.

One of my remotes is 10.0.0.0 255.255.0.0 so I entered 10.0.0.0/16 in the Network.  You can use anything descriptive in the route name.

If you remote network is a class C (like 192.168.1.0 255.255.255.0) then you would enter 192.168.1.0/24 in the Network.

(Make sure you click Update after you make your changes)

---

### Post by salsafyren on 2005-08-09
[QUOTE=flyinglizard]What do you have selected on the Routing tab?
[/QUOTE]

I have selected the "Client to LAN" radio button. I have no networks added there.

[QUOTE=flyinglizard]
One of my remotes is 10.0.0.0 255.255.0.0 so I entered 10.0.0.0/16 in the Network.  You can use anything descriptive in the route name.

If you remote network is a class C (like 192.168.1.0 255.255.255.0) then you would enter 192.168.1.0/24 in the Network.

(Make sure you click Update after you make your changes)[/QUOTE]

The remote network is a class B network (172.16.2.X). I have tried to add 172.16.2.0/8 and 172.16.2.0/16 but the client fails: 

```
ip route add '172.16.2.0/16' dev 'ppp0'
RTNETLINK answers: Invalid argument

pptpconfig: command failed, exit code 2
pptpconfig: DNS changes made to /etc/resolv.conf
pptpconfig: connected
```

Have I entered it correctly?

/Chris

---

### Post by flyinglizard on 2005-08-10
172.16.2.X is a class C network,  try /24  or use 172.16.0.0/16 for a class B network.

---

### Post by salsafyren on 2005-08-10
I entered 172.16.0.0/16 and it worked. I could connect via rdesktop 'IPADDRESS'.

However the performance was very bad, not very usable.

I have to use Windows XP, I guess.

Thanks flyinglizard.

/Chris

---

