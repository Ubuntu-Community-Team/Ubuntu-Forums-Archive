---
title: "Configuring Network Settings thru terminal"
date: 2007-01-02
forum: General Help
---

### Post by textguru on 2007-01-02
I have installed Ubuntu Server 6.06 on one of my machine. I need to change its IP address but I dont know how. Need your advise.

---

### Post by jblebrun on 2007-01-02
> **textguru said:**
> I have installed Ubuntu Server 6.06 on one of my machine. I need to change its IP address but I dont know how. Need your advise.

You'll need to use the program called **ifconfig**

I suggest you google it, or read the man page, because you can do a lot with ifconfig. But, for what you want to do, you'll need to simply use:

ifconfig <interface> <IP>

For example, for your first ethernet device, use something like

ifconfig eth0 192.168.1.114

You'll need to specify a default route, too. For example, if your router is 192.168.1.1 use

route add default 192.168.1.1

If you'll always be assigning a static IP to this interface, you should set it up in /etc/network/interfaces. This way you can specify the default route, too.

---

### Post by kd7swh on 2007-01-02
dhcpcd is a good dhcp client (text based) if you want a static ip you can also use ifconfig.

to install dhcpcd (if universal repos. are enabled)
```
sudo apt-get install dhcpcd
```

if you need help with ifconfig
```
man ifconfig
```

---

### Post by textguru on 2007-01-09
Cant change the ip address. Please help me. Here is the scenario. I have the following configuration:

IP Address: 10.0.0.1
SubNet Mask: 255.255.255.0
Gateway: 10.0.0.100
DNS: 10.0.0.10

I want to change to the following config:

IP Address: 192.168.0.10
SubNet Mask: 255.255.255.0
Gateway: 192.168.0.254
DNS: 192.168.0.100

Please post the exact terminal commands so I may pattern it.

---

### Post by dcstar on 2007-01-10
> **textguru said:**
> Cant change the ip address. Please help me. Here is the scenario. I have the following configuration:

IP Address: 10.0.0.1
SubNet Mask: 255.255.255.0
Gateway: 10.0.0.100
DNS: 10.0.0.10

I want to change to the following config:

IP Address: 192.168.0.10
SubNet Mask: 255.255.255.0
Gateway: 192.168.0.254
DNS: 192.168.0.100

Please post the exact terminal commands so I may pattern it.

sudo nano /etc/network/interfaces

---

### Post by textguru on 2007-01-11
If I am using a server, when can this take effect? after restart or immediately?

---

### Post by kd7swh on 2007-01-12
I would think it would take effect upon restart.

---

### Post by CyberCam on 2007-01-12
The easiest way to edit manage files on a non gui linux box is using midnight commander. To do this make sure you have the universe repos  enabled and installed midnight commander.
```
sudo apt-get install mc 
``` 

To use midnight commander to edit files (with root privileges) use this command
```
sudo mc
```

Now getting to the original point of changing your dhcp ip address to a static one, you need to edit the **interfaces** file in /etc/network, [COLOR="Red"]but first make a copy and name it **interfaces.default**[/COLOR]... F5 should do the trick.

You can change the code of the original file to look something like this
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.254
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers [what ever your name server ip's are]
```

Then hit F2 to save the file and exit mc (F10), then type this command in the console to have take effect
```
sudo /etc/init.d/networking restart
```

Now you should be good to go!

---

### Post by abc1987 on 2007-01-22
How would I get Ubuntu to use dhcpcd by default instead of dhclient? I install dhcpcd, but it still insists on using dhclient at boot. This is a problem for me since dhclient doesn't work properly on the university network to which I am connected!!

Please help!!

---

