---
title: "/etc/network/options cant find file"
date: 2006-11-30
forum: General Help
---

### Post by Bill007 on 2006-11-30
My small but big question 

I have a working server edgy 6.10 base system working well 

What I now want is to be able to do is

Below 
      |
      |
      v

 internet cards eth0  ( static  192.168.1.4 ) server is working on the net getting down loads for installation and other mods  so good here


What I want to do is run a network thru and provide internet via   eth1(static 192.168.2.100 )

How do I route the internet packet  from **eth0** to **eth1**

Network settings

**sudo nano /etc/network/interfaces**

# The loopback network interface

auto lo eth0 eth1
iface lo inet loopback

# The primary network interface

iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

iface eth1 inet static
        address 192.168.2.100
        netmask 255.255.255.0
        broadcast 192.168.2.255
        network 192.168.2.0



 

my server so i can

---

