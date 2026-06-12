---
title: "Http hosted website cannot be accessed via hostname (only by IP)"
date: 2024-01-31
forum: General Help
---

### Post by jefazo92 on 2024-01-31
Hi, I have a website which can only be accessed by the devices in my LAN. For some reason the website can only be accessed through the IP (not public facing ip address) but if I try with the hostname I get connection refused. I have DHCP enabled so that my devices leases IPs to the connected devices. I have checked that the port is open and listening. My /etc/dnsmasq.conf has the following config:


```
interface=apX
dchp-range= least ip, highest ip, mask, 24h
address=/domain-name/domain-IP
dhcp-option=12,domain-name
dhcp-option=114,http://domain-name/

```

and /etc/hosts/ has (for IPv4) the following configuration:


```
127.0.0.1 localhost
domain-IP domain-name

```

Does anyone know why the resolve process is not working for my ip address? I would really appreciate your help.

---

### Post by TheFu on 2024-01-31
For every system, the /etc/hosts file needs to have the IP NAME you want to use.  
Or
There needs to be a DNS server running and the clients need to point at that DNS server in their network configurations AND that needs to be reflected in each client's /etc/resolv.conf file.  dnsmasq can do that, but I don't think it is configured the way you show.  My dnsmasq setups (primary and failover) have a host table that gets used for DNS.
Or
use avahi on all the systems which implements mDNS.  In that case, each computer announces itself on the network.  The names for avahi are "{hostname}.local" - and all the systems need to run avahi/zeroconf/Bonjour <--- these are all the same service, just different OSes call them different things.

To be clear with examples.
```
# domain-IP FQDN, not just domainname.
# 1.2.3.4    hostname       hostname.domain.lan
1.2.3.4    regulus       regulus.canonical.lan
```


FQDN is the hostname+domainname.  And the domainname is the DNS domainname, not some other domain ... there are lots of other sorts of domains in computing, all the others are completely unrelated.

I almost forgot, while you shouldn't need to touch it, the /etc/nsswitch.conf controls the order that name lookups happen.
```
# hosts:          files mdns4_minimal [NOTFOUND=return] dns mymachines   # this is the original line
hosts:          files dns   # is the line I modified to prevent Avahi from being used.
```
If you want mdns to be used, the original line is better.

---

### Post by SeijiSensei on 2024-01-31
The quickest solution is to set up a local DNS server and push it to all the clients via DHCP. Or you can manually edit /etc/hosts on every machine including Windows machines where it lives as C:\Windows\System32\Drivers\etc\hosts. That's a lot more tedious work than using DNS.

---

### Post by avidandrew on 2024-02-01
What is the HTTP server config (and which HTTP server are you using)? Some, such as apache2, can be configured via a VirtualHost directive to respond to only specific hostnames or IP addresses.

---

