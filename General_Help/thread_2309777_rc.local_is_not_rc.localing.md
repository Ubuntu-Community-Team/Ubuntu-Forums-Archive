---
title: "rc.local is not rc.localing"
date: 2016-01-13
forum: General Help
---

### Post by vperaino on 2016-01-13
Alright, so I'm trying to get a couple of commands run on boot to make sense of my network situation.

My Xubuntu installation is the only installation on this machine (of which there are several) that seems to think my main ethernet interface is eth2 instead of eth0, so it constantly assigns the default route to the wrong network. Relatedly, if anyone could tell me how to permanently fix this, that would be great. 

On startup, I have to constantly run these two commands:

```

sudo route del default
sudo route add default gw 192.168.2.5
```

I thought that I could tuck them away into a script file (just stored it in /etc/routeadd), run a chmod 0700 on the file, and then add the absolute path to rc.local in order to have the script run on startup. 

Obviously it's not working, or else I wouldn't be here. 

Am I rc.localing incorrectly?

---

### Post by TheFu on 2016-01-13
/etc/udev/rules.d/70-persistent-net.rules

controls which MAC is assigned to which eth? number.

For networking, adding routes should be part of the pre-up/post-up stanzas in /etc/network/interfaces.  Of course, this means network manager ain't used.
Don't use sudo with programs run as root already - everything in /etc/rc.local runs as root.

If the only issue is that the default route isn't being set correctly, that is control in the /etc/network/interfaces file and doesn't need any special help 99.9999% of the time.

---

### Post by vperaino on 2016-01-13
> **TheFu said:**
> /etc/udev/rules.d/70-persistent-net.rules

controls which MAC is assigned to which eth? number.

I don't think my build is assigning routes based on this, though. I've tried changing these and it seems to still assign the default route to the wrong NIC. 

> For networking, adding routes should be part of the pre-up/post-up stanzas in /etc/network/interfaces.  Of course, this means network manager ain't used.
Don't use sudo with programs run as root already - everything in /etc/rc.local runs as root.

If the only issue is that the default route isn't being set correctly, that is control in the /etc/network/interfaces file and doesn't need any special help 99.9999% of the time.

If I add the route configuration to the interfaces file, is this going to conflict with the network manager somehow? 

I'm still a little lost on the relationship between Debian's manual network config files and the network manager.

---

### Post by Habitual on 2016-01-13
Don't need 'sudo' in /etc/rc.local
```
route del default
route add default gw 192.168.2.5
```

/path/to/route may be required.

---

### Post by TheFu on 2016-01-13
> **vperaino said:**
> I don't think my build is assigning routes based on this, though. I've tried changing these and it seems to still assign the default route to the wrong NIC. 



If I add the route configuration to the interfaces file, is this going to conflict with the network manager somehow? 

I'm still a little lost on the relationship between Debian's manual network config files and the network manager.

routes are not assigned based on the udev rules files. Only the ethernet devices are. You complained about eth3. Clean up that file and it can be eth0, if you like.
For non-standard network needs, network manager is worthless, IMHO. Purge it (I've been purging network manager from my systems for years) for machines that don't move and setup static IPs in the interfaces file. There is a nice manpage for that plus thousands of examples online for a simple config.  Try something. If it doesn't work, post what you've tried and we can help.

Or do it the brute-force method inside the rc.local, but that won't let *service networking restart* and other service restart cmds which depend on networking being restarted work correctly.

Don't have a clue what debian has to do with this question.

---

### Post by SeijiSensei on 2016-01-13
> **Habitual said:**
> Don't need 'sudo' in /etc/rc.local
```
route del default
route add default gw 192.168.2.5
```

/path/to/route may be required.

^This.  /etc/rc.local runs with root privileges by default.  You do not need, nor should you use, sudo.

---

### Post by vperaino on 2016-01-13
> **TheFu said:**
> routes are not assigned based on the udev rules files. Only the ethernet devices are. You complained about eth3. Clean up that file and it can be eth0, if you like.
For non-standard network needs, network manager is worthless, IMHO. Purge it (I've been purging network manager from my systems for years) for machines that don't move and setup static IPs in the interfaces file. There is a nice manpage for that plus thousands of examples online for a simple config.  Try something. If it doesn't work, post what you've tried and we can help.

Or do it the brute-force method inside the rc.local, but that won't let *service networking restart* and other service restart cmds which depend on networking being restarted work correctly.

Don't have a clue what debian has to do with this question.

I think I was unclear in my original post. 

My NICs are designated correctly in the udev rules file. I have three different NICs in my machine, which are all connected to physically separate networks. What's incorrect is that the default route is always being assigned to eth2 which is on the 192.168.3.x network, whereas I want the default route to be on eth0 which is connected to the 192.168.2.x network (the third network is just a local DHCP to my machine for doing quick gigabit ethernet file transfers, since our office network isn't gigabit).

Basically, I'm trying to figure out the easiest way of telling my machine, "I want the default gateway to be 192.168.2.5". I was wanting to use rc.local as a simple solution but if there's an even more basic fix (like editing the udev rules file would be for switching NIC names), I'm down for that as well. I don't know what service/process/file tells the system what the default route is, dynamically.

---

### Post by TheFu on 2016-01-13
Please post, using code tags, the output from 
* ifconfig
* route
* cat /etc/network/interfaces

Thanks.  For a non-trivial network setup like yours, network-manager IS NOT your friend, IMHO.

I think the "best" answer for your requirements is to edit the /etc/network/interfaces file. It is also the most standard.

---

### Post by vperaino on 2016-01-13
> **TheFu said:**
> Please post, using code tags, the output from 
* ifconfig
* route
* cat /etc/network/interfaces

Thanks.  For a non-trivial network setup like yours, network-manager IS NOT your friend, IMHO.

I think the "best" answer for your requirements is to edit the /etc/network/interfaces file. It is also the most standard.

Here ya go. I was mistaken typing earlier, it's the eth1 network that is getting the default route for 192.168.3.0, not eth2. 

```
eth0      Link encap:Ethernet  HWaddr 00:1a:92:95:54:1c            
          inet addr:192.168.2.118  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe95:541c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:979522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:773475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:720660798 (720.6 MB)  TX bytes:86934562 (86.9 MB)
          Interrupt:20 


eth1      Link encap:Ethernet  HWaddr 00:00:e8:18:bc:60  
          inet addr:192.168.3.34  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe18:bc60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:964061 (964.0 KB)  TX bytes:1634864 (1.6 MB)


eth2      Link encap:Ethernet  HWaddr 00:90:47:00:6b:6c  
          inet addr:192.168.4.1  Bcast:192.168.4.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

Here is my routing table after having manually made the edit with the "route" commands. Normally, the default route when I first boot is 192.168.3.8. 

```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.5     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.3.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
192.168.4.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2

```

There is currently no configuration in my /etc/network/interfaces file, just the loopback.

---

### Post by TheFu on 2016-01-13
Are all these IPs DHCP or are they static - i.e. provided for this system by the network administrator? Sorry - should have asked that before.

```

auto eth0
# if DHCP, use the next line, but remove the "static" one and all that follows it
#iface eth0 inet dhcp
# if static, use something like this (edited for your local needs); 
# add a separate stanza for each network device ... eth0, eth1, eth2, eth ..... 99
#  don't forget the 'auto eth0' above. This is needed regardless for any NIC to 
#  start with the system.
iface eth0 inet static
  address 172.22.22.11
  gateway 172.22.22.1
  netmask 255.255.255.0
  dns-nameservers 172.22.22.1

```

Do not remove/touch the lo0 and loopback parts of the file.

You can add metric to the stanza to control things.  If there isn't a gateway for the local-only subnets, that is fine.
If you need more details about this stuff, the manpage is pretty good.  **man interfaces**


For anything NICs in the interfaces file, network-manager shouldn't try to handle them. If it does, just purge those packages.  If this machine is portable, I would leave network-manager, but I wouldn't if it never moves or moves once a year.

---

### Post by vperaino on 2016-01-13
This is a desktop machine, so it's not going anywhere. 

eth0 and eth1 are on DHCP networks, eth2 actually hosts a DHCP server. 

I'm not sure I understand how setting up the interfaces file is going to tell my system what the default gateway is. For example, normally I want all my browser traffic running through eth0 and the 192.168.2.0 network because 192.168.2.5 (the address of our firewall) is the normal routing point for that traffic. However, if I need to get in the SIP network, I can manually input a 192.168.3.0 address into my browser and it will go to one of our local network phones via eth1 where I can make adjustments.

---

### Post by TheFu on 2016-01-13
It will.

There is a gateway setting for each card. That makes route settings, based on the netmask and IP address for the card. Standard networking.
Of course, with DHCP, that will be ignored, so you'll need to add post-up sections for the NICs that need more routing help. There are examples in the manpages OR you can post your newly created interfaces file with your attempt to solve this and we can help. Don't forget that priority is controlled via the **metric** setting for each NIC (not in my example). This is also standard networking stuff.

Or am I completely missing what you need?  There aren't many network configurations that cannot easily be handled by the interfaces file.  If you don't want to use it, fine.

---

### Post by vperaino on 2016-01-13
What I'm asking is how does the interfaces file specify the default route? Doing a quick search shows me some syntax for the interfaces file that generally goes:

```
up route add 192.168.2.5 dev eth0
up route add default gw 192.168.2.5
```

Is this what I would add to my interfaces file? 

As it stands, my computer is assigning the default route to the 192.168.3.0 network on boot and I'm not sure what's controlling that; if I could change that policy I would be golden, regardless of whether I can do it in the interfaces file or some other way.

---

### Post by TheFu on 2016-01-14
Answered in post #10.

---

### Post by vperaino on 2016-01-14
I don't need my routes defined for the interfaces themselves, though, I need the default route designated for the whole system. 

Right now when I boot, I get this, which causes my internet connection to fail. 

[IMG]http://i.imgur.com/2jdVrsj.png[/IMG]

I need it to be this. 

[IMG]http://i.imgur.com/A8OAhpg.png[/IMG]

Presently, every single time I log on, I have to enter this command to rectify the situation. 

```

sudo route del default
sudo route add default gw 192.168.2.5
```

That's why I was trying to use rc.local in the first place, to automate that command on boot.

---

### Post by SeijiSensei on 2016-01-14
Look again at post #10.  Specify the network information for each interface in /etc/network/interfaces, and in the stanza for eth0 specify "gateway 192.168.2.5".  Do not specify a gateway for any other interface.  Avoid using DHCP for "multi-homed" machines like this; use static addressing.

---

### Post by vperaino on 2016-01-14
> **SeijiSensei said:**
> Look again at post #10.  Specify the network information for each interface in /etc/network/interfaces, and in the stanza for eth0 specify "gateway 192.168.2.5".  Do not specify a gateway for any other interface.

That's why I said I wasn't sure that I understood completely. 

So if I specify a gateway for just one interface (eth0) in the **interfaces** file, even if the syntax is nested under the eth0 section, that becomes the system's default gateway?

Also, my eth0 connects via dhcp. Does entering a gateway still affect it?

---

### Post by SeijiSensei on 2016-01-14
Yes, there should be only one gateway.  It's the machine to which traffic is sent for which there is no local subnet.  

The DHCP server should give you a gateway.  However, as I said, I would never use DHCP to assign addresses on a multi-homed system like this.  The router should let you specify a range of addresses in the subnet that are assigned by DHCP so that others are available for static assignments.  Use an address outside the DHCP-assigned range.

---

### Post by vperaino on 2016-01-15
Alright, so I purged Network Manager (because honestly I've wanted to do that for a while), then changed my interfaces file to this: 

```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
    address 192.168.2.90
    netmask 255.255.255.0
    gateway 192.168.2.5
    dns-nameservers 8.8.8.8


auto eth1
iface eth1 inet static
    address 192.168.3.200
    netmask 255.255.255.0


auto eth2
iface eth2 inet static
    address 192.168.4.1
    netmask 255.255.255.0
```

...And that seemed to do the trick! 

Thanks for helping me understand this process a little better. :)

EDIT: Technically my original problem with rc.local remains unsolved, but I fixed my actual underlying issue, so I'm marking the thread as "solved" anyway.

---

### Post by SeijiSensei on 2016-01-15
Unless there was another problem that we missed, it was your use of sudo in rc.local that was the issue.

---

### Post by vperaino on 2016-01-15
> **SeijiSensei said:**
> Unless there was another problem that we missed, it was your use of sudo in rc.local that was the issue.

I didn't actually use sudo in my rc.local file, the "sudo" was just an example of how I would type it into the terminal manually after booting.

---

### Post by TheFu on 2016-01-18
> **SeijiSensei said:**
> Unless there was another problem that we missed, it was your use of sudo in rc.local that was the issue.

Thanks for explaining it a little differently SeijiSensei. 

Sometimes folks need to hear the same thing from multiple sources, each with a slightly different angle to believe it. Sad that it took extra days to get there. I'm stubborn that way to, sometimes. ;)  

I think the root issue in the rc.local was not following best scripting practices and using full-path-to-programs everywhere. /usr/bin/sudo and /sbin/route are likely what was needed. Alas, THAT was not the "best answer" for the real problem, hence my push for doing it in the *interfaces* file - which **is** the correct way to solve this issue.

Of course, there are 100 different ways to get this sort of thing working. Often there isn't really any "best" way, but in this situation, there is ... the *interfaces* file. This integrates with service start/stop commands, unlike other possible solutions. 

IMHO.

Regardless, happy it is working.

---

