---
title: "Problem autoupdate DNS by DHCP"
date: 2005-05-23
forum: General Help
---

### Post by praenti on 2005-05-23
Hi,

I have two computers, the bigger one is the server, the smaller one the client.
I have installed Hoary Kubuntu.

Now I want that the client gets an IP adress from the DHCP (is working) and register the name by the DNS (not working) so I can easily reach the machine by name.
The problem is that I cannot see any update request on the DNS (bind9 package)

First let me describe what I have done:
1. generate a key with "dnssec-keygen -a HMAC-MD5 -b 128 -n USER DHCP_UPDATER"
2. add following line to /etc/dhcp3/dhcpd.conf:
ddns-update-style interim;
ddns-domainname "intern";
update-static-leases true;
key DHCP_UPDATER {
     algorithm HMAC-MD5.SIG-ALG.REG.INT;
     secret <mykey>;
};
zone intern. {    
     primary 10.180.7.2;    
     key DHCP_UPDATER;
}
authoritative;

3. add following lines to named.conf:
auth-nxdomain yes;
key DHCP_UPDATER {
     algorithm HMAC-MD5.SIG-ALG.REG.INT;
     secret <mykey>
};
on each zone this one: allow-update { key DHCP_UPDATER; }; and notify yes;


On the client I changed /etc/dhcp3/dhclient.conf and set
send host-name "schul-client155">;


But no update is done on the zones  :-| . Can anybody help me and give me a hint?

Cheers,
Michael

---

