---
title: "Running KVM without root privileges"
date: 2007-08-17
forum: General Help
---

### Post by ozonblue on 2007-08-17
Hi .

I'm trying to run KVM  on Feitsy, 64 bit Intel with the "-net nic -net tap" switches so I can use it in bridged network mode.

It refuses and I have to run it sudo which for security concerns I don't want to do.

The error message is : "warning: could not configure /dev/net/tun: no virtual network emulation
Could not initialize device 'tap''

I have googled everywhere on the net todo with debian/ubuntu and thes messages and have tried every trick in the book: I have even changed udev settings so that the permissions on /dev/net/tun are ok for non-root users. Nothing helps.

regards,

Eugene

---

### Post by ozonblue on 2007-08-21
Ok - I found a solution on Ubuntu Feisty:

Based on 
[this link]("http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/FrequentlyAskedQuestions#head-2511814cb92c14dbe1480089c04f83c281117a86")

the problem with Linux 2.6.18 and up is the  CAP_NET_ADMIN capability associated with persistent tap interfaces.  

Using tunctl to bring up a tap interface in a wrapper script for kvm:


1)  apt-get install bridge-utils  uml-utilities

2) The /etc/network/interfaces file:

> 
auto lo eth0 br0

# The loopback network interface

iface lo inet loopback

# The bridge interface

iface br0 inet dhcp
        bridge_ports eth0
        bridge_maxwait 2
        up /sbin/ifconfig eth0 inet 0.0.0.0 promisc


# The primary network interface

iface eth0 inet static
        address 192.168.0.129
        netmask 255.255.255.0



3) Add to /etc/udev/rules.d/40-permissions.rules file:

> 
KERNEL=="tun",                          MODE="0666"


4) Modify /etc/kvm/kvm-ifup file:

> 
#!/bin/sh
switch=$(ip route list | awk '/^default / { print $NF }')
sudo ifconfig $1 0.0.0.0 up
sudo brctl addif ${switch} $1


5) Wrapper script for KVM:

> 
#!/usr/bin/env bash
# script to manage tap interface allocation
# for linux kernels >= 2.6.18

# set up a tap interface for qemu
# USERID - uid qemu is being run under.
USERID=`whoami`

# generate a random mac address for the qemu nic
# shell script borrowed from user pheldens @ qemu forum

ranmac=$(echo -n DE:AD:BE:EF ; for i in `seq 1 2` ; \
do echo -n `echo ":$RANDOM$RANDOM" | cut -n -c -3` ;done)

# specify which NIC to use - see qemu.org for others
# model=r8169
iface=`sudo tunctl -b -u $USERID`

# start kvm with our parameters
echo "Bringing up interface $iface with mac address $ranmac"
kvm -no-acpi -m 384 -net nic,vlan=0,macaddr=$ranmac -net tap,vlan=0,ifname=$iface -no-reboot $@ /virtual/kvm/winxp.img

# qemu has stopped - no longer using tap interface
sudo tunctl -d $iface &> /dev/null


regards,

Eugene Coetzee

---

