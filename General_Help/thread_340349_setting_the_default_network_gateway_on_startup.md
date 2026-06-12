---
title: "setting the default network gateway on startup"
date: 2007-01-17
forum: General Help
---

### Post by tr333 on 2007-01-17
i need to set the network gateway on startup for my server with the command:
```
route add default gw xxx.xxx.xxx.xxx
```
i have read some posts on the forums that say startup scripts should be put in /etc/init.d with a symlink from /etc/rc2.d, or possibly rc.local.  what is the best way to set the network gateway on startup?

---

### Post by maggotbrain on 2007-01-17
I am sure that there are many ways to skin this cat....
My preference is to put the default gateway entries into the file /etc/network/interfaces.

Here is an example:

iface eth0 inet static
address 192.168.0.4
netmask 255.255.255.0
**gateway 192.168.0.1**

---

### Post by tr333 on 2007-01-17
i already have it in there, but it doesnt seem to set the gateway on system startup.
it sets the ip address tho...

```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 225.225.225.0
broadcast 192.168.0.255
gateway xxx.xxx.xxx.xxx
```

---

### Post by hayesey on 2007-01-17
is the gateway address on the same subnet as the server?  I don't know why you've bothered blanking the addresses out when it would appear to be a private '192.168..." address range!

Anyway, adding these lines to the end of your interfaces file will setup a route, and delete the route when the interface is taken down:

```

up route add **same as route command**
down route del **same as route command**

```

---

### Post by tr333 on 2007-01-17
> **hayesey said:**
> is the gateway address on the same subnet as the server?  I don't know why you've bothered blanking the addresses out when it would appear to be a private '192.168..." address range!

Anyway, adding these lines to the end of your interfaces file will setup a route, and delete the route when the interface is taken down:

```

up route add **same as route command**
down route del **same as route command**

```

i tried that, but it didnt seem to set the gateway on startup.

the server address is 192.168.0.2 and the gateway is 192.168.0.254, so i'm guessing that they are on the same subnet.

---

### Post by maggotbrain on 2007-01-17
# The primary network interface
auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask **225.225.225.0**
broadcast 192.168.0.255
gateway xxx.xxx.xxx.xxx[/code][/QUOTE]

I hope that is a typo you have entered for the netmask. It should read 255.255.255.0

---

### Post by tr333 on 2007-01-18
> **maggotbrain said:**
> # The primary network interface
auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask **225.225.225.0**
broadcast 192.168.0.255
gateway xxx.xxx.xxx.xxx[/code]

I hope that is a typo you have entered for the netmask. It should read 255.255.255.0

thanks for the help with this problem...

i thought i read the contents of that file at least 30+ times, and i didnt notice that...
it seems to be working now :D 

any idea why i could set the gateway manually with this error in the file?

---

### Post by technodigifreak on 2007-01-18
> **tr333 said:**
> thanks for the help with this problem...

i thought i read the contents of that file at least 30+ times, and i didnt notice that...
it seems to be working now :D 

any idea why i could set the gateway manually with this error in the file?

You could probably save the file just fine, but if you manually restarted networking with */etc/init.d/networking restart* - it should have returned an error stating invalid subnet mask.  But if you simply rebooted, you may not have noticed the error in a verbose boot.

---

