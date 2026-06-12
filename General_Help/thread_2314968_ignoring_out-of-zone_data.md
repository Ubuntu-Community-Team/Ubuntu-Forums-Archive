---
title: "ignoring out-of-zone data"
date: 2016-02-25
forum: General Help
---

### Post by decentandsimple2 on 2016-02-25
Hey All

Configured the bind9 in ubuntu. I am able to resolve only name server ip to name and name to ip. But when i try to resolve other host name it gives me this error 

**** server can't find mail.ashiatech3.net: NXDOMAIN**

When I checked named-checkconf I got this error

[B]/etc/bind/zones/db.ashiatech3:16: ignoring out-of-zone data (mail.ashiatech3.net)
/etc/bind/zones/db.ashiatech3:17: ignoring out-of-zone data (c7.ashiatech3.net)[/B]

This are the details of zone files 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Reverse Zone File
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.ashiatech3.net. admin.ashiatech3.net. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
                IN      NS      ns1.ashiatech3.net.
133.0           IN      PTR     ns1.ashiatech3.net.
134.0           IN      PTR     mail.ashiatech3.net.
137.0           IN      PTR     c7.ashiatech3.net.
--------------------------------------------------------------------------
Forward Zone File

@       IN      SOA     ns1.ashiatech3.net. admin.ashiatech3.net. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
; name server -NS records
                        IN      NS      ns1.ashiatech3.net.
; name server - A records
ns1.ashiatech3.net.     IN      A       192.168.0.133
; Other Server - A Records
mail.ashiatech3.net.    IN      A       192.168.0.134
c7.ashiatech3.net.      IN      A       192.168.0.137
----------------------------------------------------------------------------------------------------.
Can any one help me out in this

Regards
Vikas Kanojia

---

### Post by SeijiSensei on 2016-02-25
Try removing the domains from the hostnames in the forward file and try again.  For instance, the last line should read
```
c7 IN A 192.168.0.137
```

---

