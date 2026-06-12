---
title: "Network config does not work"
date: 2006-12-18
forum: General Help
---

### Post by telovoyagarcar on 2006-12-18
i just reinstalled Ubuntu from scratch... 
I saved the /etc/network/interfaces file among others in the backup.
So now i am overwritting the default file with this one, which was the one working before.. and i can't access the net.
I can see my router and use its interface.. but not go out.
The gnome network configuration tool does not help neither, and i can see that what it actually does is to modify the same interfaces file.

Where else does ubuntu keeps this basic configuration?

this is the configuration... i see no reason why it does not work.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.21
netmask 255.255.255.0
network 192.168.2.1
broadcast 192.168.2.255
gateway 192.168.2.1
nameserver 192.168.2.1





```




thanks

---

### Post by fragos on 2006-12-18
Do you have the Network Monitor applet running.  It will tell you which connection is active as well as IP and activity information.  Perhaps your connection name changed to "lo" and you need to select "eth0".  Theer's also a configure button which gives you entry the network configuration.  The only parameters you should have to set for broadband is which port is active and DHCP wich appears to be up because you have a NAT local IP.  Also, have you powered down the machine and the modem and tried restarting both?.  Lastly, if you're running DSL you may need PPPOE.

---

### Post by hanzomon4 on 2006-12-19
Could be the DNS I had this issue a while back here's what I did:
> **hanzomon4 said:**
> I fixed it.. here's how

First the only setting I had to reset after a reboot was the DNS. The config file where the DNS settings are stored is in /etc/resolv.conf. 
For some reasons getting my settings to stick using the Network configuration tool would not work, so I tried editing /etc/resolv.conf by hand.
That did not work because Ubuntu uses a dynamic DNS configuration. This will overwrite the etc/resolv.conf file at boot-up.
The solution is to add your settings to /etc/resolvconf/resolv.conf.d/base like this.
```
 sudo gedit /etc/resolvconf/resolv.conf.d/base
```
```
nameserver   192.X.X.X
```
Replace the "192.X.X.X" with your DNS number.

Okay my work here is done.

---

