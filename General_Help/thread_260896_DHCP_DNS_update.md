---
title: "DHCP DNS update"
date: 2006-09-19
forum: General Help
---

### Post by subscr on 2006-09-19
Hi,

I am trying to migrate from RHEL to Dapper 6.0.6 LTS. I have configured the DHCP and Bind on Dapper. When I try to use the settings that I had on RHEL for DNS updates of assigned DHCP addresses, I get errors that the flags are invalid. 

RHEL Named version - BIND 9.2.2
RHEL DHCP Server Version - Internet Systems Consortium DHCP Server V3.0.1

Dapper Named Version - named 8.4.6-REL-NOESW Tue Feb  1 10:10:48 UTC 2005
Dapper DHCPD version - DHCP Server 2.0pl5

The following settings in dhcpd.conf don't work in Dapper.

allow client-updates;
ddns-update-style interim;
key "rndc-key" { Some Secret }; 

Zone definitions

In plain words, I am looking for help in trying to get DHCP automatically update the DNS Server once a lease is granted.

Thanks
Partha

---

### Post by lawina on 2006-10-10
Please put this question in the Ubuntu server forum.

[http://www.ubuntuforums.org/forumdisplay.php?f=7](http://www.ubuntuforums.org/forumdisplay.php?f=7)

---

