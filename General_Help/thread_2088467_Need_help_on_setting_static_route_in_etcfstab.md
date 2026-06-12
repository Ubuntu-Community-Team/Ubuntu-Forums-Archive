---
title: "Need help on setting static route in /etc/fstab"
date: 2012-11-26
forum: General Help
---

### Post by vcrpcant on 2012-11-26
Hi,

Hi have two ubuntu 10.04 machines
both have two NIC's

in both machines
one NIC is connected to the lan router
the other NIC is connected via crossover cable to the other ubuntu computer
and vice-versa

Both machines cannot ping through the router, because they are on different vlan's

my goal is to access one of the machines while I am working at the other

the reason I want to use the crossover cable is because both NIC's in both ends are 10/100/1000
I don't want to connect through the router because it's only 10/100

I have tried playing around with fstab following some instructions in some sites, but no luck

can somebody shed some light in here?:confused:
posting an fstab example would be great

---

### Post by dannyboy79 on 2012-11-26
fstab has nothing to do with routing ethernet traffic. that's for mounting partitions, hard drive storage during boot up. You need to play around with iptables to route traffic to the appropriate nic. I wouldn't be able to help with that, just wanted to clarify that fstab is NOT what you need to edit.

---

### Post by Habitual on 2012-11-26
> **dannyboy79 said:**
> ...fstab is NOT what you need to edit.

What "he" said.

Where you read is just as important as what you read, so I'd suggest
[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html) (search for "static routes") 
and learn to make backups, I have a hunch you'll need them.

---

### Post by dcstar on 2012-11-27
> **vcrpcant said:**
> Hi,

Hi have two ubuntu 10.04 machines
both have two NIC's
........
my goal is to access one of the machines while I am working at the other
........

Then simply assign static IP address in the same subnet on the two interfaces connected to each other.

---

### Post by efflandt on 2012-11-27
If you connect 2 computers with crossover cable and assign them each an IP in a subnet that is not on any other interface on either computer, you do not need any routing or gateway or DNS for that at all.  All you need is IP and netmask

For example:

1. IP 172.16.0.1, netmask 255.255.255.0
2. IP 172.16.0.2, netmask 255.255.255.0

If 1 connects to 172.16.0.2 it will find it using arp
If 2 connects to 172.16.0.1 it will find it using arp
No routing necessary because they are both on same subnet.

The only thing is, if running a firewall on either machine you would need to open a hole for that interface or those IP addresses.

---

### Post by vcrpcant on 2012-11-27
Thanks, guys! I've done it:)

I must have been sleeping when I wrote /etc/fstab, what I ment was /etc/network/interfaces

A special thanks to efflandt for putting me in the right direction

I was trying to do this on the same subnet and to make things more complicated, I was thinking I needed static route to host, which I did not at all because this two machines are already separated in different vlan's by the router as I said in my post


Here's the /etc/network/interfaces files for both machines:

######### COMPUTER 1 #########
######### /ETC/NETWORK/INTERFACES ######### 
auto lo
iface lo inet loopback

auto eth0
    iface eth0 inet static
    address 192.168.27.2
    gateway 192.168.27.1
    network 192.168.27.0
    netmask 255.255.255.0


auto eth1
    iface eth1 inet static
    address 192.168.30.12
    netmask 255.255.255.0



######### COMPUTER 2 #########
######### /ETC/NETWORK/INTERFACES #########
auto lo
iface lo inet loopback

auto eth0
    iface eth0 inet static
    address 192.168.27.3
    gateway 192.168.27.1
    network 192.168.27.0
    netmask 255.255.255.0


auto eth1
    iface eth1 inet static
    address 192.168.30.11
    netmask 255.255.255.0


Regards!!!!!!!!  :guitar:

---

