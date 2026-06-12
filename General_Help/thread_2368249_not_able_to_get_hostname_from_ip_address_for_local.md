---
title: "not able to get hostname from ip address for local IPs"
date: 2017-08-08
forum: General Help
---

### Post by fuadk on 2017-08-08
Hi, 
I have gateway installed on Ubuntu, and not able to get hostname for local IPs, using nslookup or programmatically using getnameinfo
nslookup gives:
```
fuad@URLF:~$ nslookup 192.168.1.107
Server:        127.0.1.1
Address:    127.0.1.1#53


** server can't find 107.1.168.192.in-addr.arpa: NXDOMAIN
```
The DNS configuration is shown below using nuclei:
```
nmcli device show|grep DNS
IP4.DNS[1]:                             41.128.225.225

```
I tried adding router as DNS using nuclei:

```
nmcli connection edit type ethernet
set ipv4.DNS 192.168.1.1
```
saved and quit but still the same
below is all the output of nmcli show:
------
```
GENERAL.DEVICE:                         bridge0
GENERAL.TYPE:                           bridge
GENERAL.HWADDR:                         70:F3:95:09:2F:D5
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     Bridge connection 1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
IP4.ADDRESS[1]:                         192.168.1.135/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             41.128.225.225
IP6.ADDRESS[1]:                         fd2c:d457:2852:1:f1c2:dc5d:d6e:6e6f/64
IP6.ADDRESS[2]:                         fe80::f965:9dc3:db65:ea36/64
IP6.GATEWAY:                            
IP6.ROUTE[1]:                           dst = fd2c:d457:2852:1::/64, nh = ::, mt = 425


GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         70:F3:95:09:2F:D5
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     bridge0 slave 2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
WIRED-PROPERTIES.CARRIER:               on


GENERAL.DEVICE:                         enp17s0
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         78:54:2E:70:07:30
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     bridge0 slave 1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
WIRED-PROPERTIES.CARRIER:               on


GENERAL.DEVICE:                         lo
GENERAL.TYPE:                           loopback
GENERAL.HWADDR:                         00:00:00:00:00:00
GENERAL.MTU:                            65536
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
IP4.ADDRESS[1]:                         127.0.0.1/8
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         ::1/128
IP6.GATEWAY:                            
```
--------

Regards,
Fuad

---

### Post by SeijiSensei on 2017-08-08
Are you using BIND9 and isc-dhcp-server to handle IP assignments and domain name resolution?  It's possible to link them together so that new machines are added automatically to the DNS server records. See [https://wiki.samba.org/index.php/Configure_DHCP_to_update_DNS_records_with_BIND9](https://wiki.samba.org/index.php/Configure_DHCP_to_update_DNS_records_with_BIND9)

Without a local DNS server, I don't know how you would resolve IPs to domain names for addresses in private IP subnets like 192.168/16.  I presume you want something more generalizable than /etc/hosts files on all the clients.

---

