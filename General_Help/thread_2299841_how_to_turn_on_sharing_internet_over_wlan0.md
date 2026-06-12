---
title: "how to turn on sharing internet over wlan0"
date: 2015-10-21
forum: General Help
---

### Post by madgon2 on 2015-10-21
how to turn on sharing internet over wlan0 becose i try share intrernet but dont work ??  ```
"/etc/network/interfaces"  auto lo iface lo inet loopback  [br]  allow-hotplug wlan0 auto wlan0 iface wlan0 inet static address 192.168.1.3  broadcast 192.168.1.255  netmask 255.255.255.0  gateway 10.10.10.1  network  192.168.1.0   # The primary network interface auto em1 iface em1 inet static address 10.10.10.3 gateway 10.10.10.1 network 10.10.10.0 netmask 255.255.255.0 broadcast 10.10.10.255 [/quote]  [quote="/etc/dhcpd.conf"] # # Sample configuration file for ISC dhcpd for Debian # # Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as # configuration file instead of this file. # #  # The ddns-updates-style parameter controls whether or not the server will # attempt to do a DNS update when a lease is confirmed. We default to the # behavior of the version 2 packages ('none', since DHCP v2 didn't # have support for DDNS.) ddns-update-style none;  # option definitions common to all supported networks... option domain-name "example.org"; option domain-name-servers ns1.example.org, ns2.example.org;  default-lease-time 600; max-lease-time 7200;  # If this DHCP server is the official DHCP server for the local # network, the authoritative directive should be uncommented. #authoritative;  # Use this to send dhcp log messages to a different log file (you also # have to hack syslog.conf to complete the redirection). log-facility local7;  # No service will be given on this subnet, but declaring it helps the  # DHCP server to understand the network topology.  #subnet 10.152.187.0 netmask 255.255.255.0 { #}  # This is a very basic subnet declaration.  #subnet 10.254.239.0 netmask 255.255.255.224 { #  range 10.254.239.10 10.254.239.20; #  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org; #}  # This declaration allows BOOTP clients to get dynamic addresses, # which we don't really recommend.  #subnet 10.254.239.32 netmask 255.255.255.224 { #  range dynamic-bootp 10.254.239.40 10.254.239.60; #  option broadcast-address 10.254.239.31; #  option routers rtr-239-32-1.example.org; #}  # A slightly different configuration for an internal subnet. #subnet 10.5.5.0 netmask 255.255.255.224 { #  range 10.5.5.26 10.5.5.30; #  option domain-name-servers ns1.internal.example.org; #  option domain-name "internal.example.org"; #  option routers 10.5.5.1; #  option broadcast-address 10.5.5.31; #  default-lease-time 600; #  max-lease-time 7200; #}  # Hosts which require special configuration options can be listed in # host statements.   If no address is specified, the address will be # allocated dynamically (if possible), but the host-specific information # will still come from the host declaration.  #host passacaglia { #  hardware ethernet 0:0:c0:5d:bd:95; #  filename "vmunix.passacaglia"; #  server-name "toccata.fugue.com"; #}  # Fixed IP addresses can also be specified for hosts.   These addresses # should not also be listed as being available for dynamic assignment. # Hosts for which fixed IP addresses have been specified can boot using # BOOTP or DHCP.   Hosts for which no fixed address is specified can only # be booted with DHCP, unless there is an address range on the subnet # to which a BOOTP client is connected which has the dynamic-bootp flag # set. #host fantasia { #  hardware ethernet 08:00:07:26:c0:a5; #  fixed-address fantasia.fugue.com; #}  # You can declare a class of clients and then do address allocation # based on that.   The example below shows a case where all clients # in a certain class get addresses on the 10.17.224/24 subnet, and all # other clients get addresses on the 10.0.29/24 subnet.  #class "foo" { #  match if substring (option vendor-class-identifier, 0, 4) = "SUNW"; #}  #shared-network 224-29 { #  subnet 10.17.224.0 netmask 255.255.255.0 { #    option routers rtr-224.example.org; #  } #  subnet 10.0.29.0 netmask 255.255.255.0 { #    option routers rtr-29.example.org; #  } #  pool { #    allow members of "foo"; #    range 10.17.224.10 10.17.224.250; #  } #  pool { #    deny members of "foo"; #    range 10.0.29.10 10.0.29.230; #  } #}  subnet 192.168.1.0 netmask 255.255.255.0 {         option routers                  192.168.1.3;         option subnet-mask              255.255.255.0;          option domain-name              "example.com";         option domain-name-servers       192.168.1.3;          option time-offset              -18000;     # Eastern Standard Time  	range 192.168.1.10 192.168.1.100; }  
```  ```
"rc.local"#!/bin/sh -e # # rc.local # # This script is executed at the end of each multiuser runlevel. # Make sure that the script will "exit 0" on success or any other # value on error. # # In order to enable or disable this script just change the execution # bits. # # By default this script does nothing.   iptables -A FORWARD -i em1 -o wlan0 -j ACCEPT iptables -A FORWARD -i wlan0 -o em1 -m state --state ESTABLISHED,RELATED -j ACCEPT iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE   exit 0
```   whats is wrong ?? becose i dont know

---

### Post by ajgreeny on 2015-10-21
Your post is totally unreadable as you did not use the correct code tags (see my signature for a How-to) but quoted which loses all formatting of the output.

I will try to edit your post to make the output make more sense, but if this does not work please run your commands again and repost with proper tags.

EDIT:
NO; it did not work as I had hoped.

Please repost using code tags.

---

### Post by ajgreeny on 2015-10-22
I see you have tried to edit your post as I asked, but unfortunately it has not helped.

Can you please run the same commands again on your system and post again, using code tags on the output of the commands that you copy into the reply window.

I'm sure we can crack this for you but we do need to see the details in a more sensible layout.

---

### Post by madgon2 on 2015-10-26
i have ubuntu server  Ubuntu 14.04.3 LTS two cards em1  and wlan0 -> (02:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter(PCI-Express) (rev 01))  

with config in: /etc/network/interfaces
```
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet static
address 10.10.10.3
gateway 10.10.10.1
network 10.10.10.0
netmask 255.255.255.0
broadcast 10.10.10.255
```

my dhcpd config
 ```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}
# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

subnet 192.168.1.0 netmask 255.255.255.0 {
        option routers                  192.168.1.3;
        option subnet-mask              255.255.255.0;


        option time-offset              -18000;     # Eastern Standard Time

        range 192.168.1.10 192.168.1.100;




```


my etc/hostapd/hostapd.conf

```
#change wlan0 to your wireless device
interface=wlan0
driver=nl80211
ssid=test
channel=11

macaddr_acl=0

accept_mac_file=/etc/hostapd.accept
deny_mac_file=/etc/hostapd.deny

```

```
~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.10.10.1      0.0.0.0         UG    0      0        0 em1
10.10.10.0      *               255.255.255.0   U     0      0        0 em1

```

sudo iptable --list
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

```

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

```


ps. my noscript extension to firefox blocked page and its make erros like in older post

---

### Post by madgon2 on 2015-10-29
solution 


[https://groups.google.com/forum/#!topic/pl.comp.os.linux/xHyvTA5qBos](https://groups.google.com/forum/#!topic/pl.comp.os.linux/xHyvTA5qBos)

rc,local:

ifconfig wlan0 192.168.1.3 netmask 255.255.255.0
iptables -t nat -A POSTROUTING -o em1 -j MASQUERADE
iptables -I FORWARD -j ACCEPT
dhcpd wlan0
sleep 10
hostapd /etc/hostapd/hostapd.conf

exit 0

---

