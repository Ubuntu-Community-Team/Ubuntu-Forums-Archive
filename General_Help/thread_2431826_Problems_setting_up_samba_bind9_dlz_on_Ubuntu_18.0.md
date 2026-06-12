---
title: "Problems setting up samba bind9_dlz on Ubuntu 18.04"
date: 2019-11-22
forum: General Help
---

### Post by b-david on 2019-11-22
I followed the following guides to setup samba as an additional active directory server to my windows server with bind9 dns:


[https://www.tecmint.com/join-additional-ubuntu-dc-to-samba4-ad-dc-failover-replication/](https://www.tecmint.com/join-additional-ubuntu-dc-to-samba4-ad-dc-failover-replication/)
[https://wiki.samba.org/index.php/BIND9_DLZ_DNS_Back_End#Troubleshooting](https://wiki.samba.org/index.php/BIND9_DLZ_DNS_Back_End#Troubleshooting)


The active directory replication works, but the dns replication does not work. When I'm running "samba_dnsupdate --all-names" I get the following output:
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
update failed: REFUSED
; TSIG error with server: tsig verify failure
update failed: REFUSED
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
; TSIG error with server: tsig verify failure
Failed update of 19 entries


Here is a list of versions:
Ubuntu: 18.04
Samba: 4.7.6-Ubuntu
bind9: 9.11.3-1ubuntu1.11-UbuntuAnd this is my smb.conf:


[global]
        netbios name = DC01
        realm = DOMAIN.COM
        server role = active directory domain controller
        workgroup = DOMAIN.COM
        dns forwarder = 172.17.1.1
        idmap_ldb:use rfc2307 = yes


        template shell = /bin/bash
        winbind use default domain = true
        winbind offline logon = false
        winbind nss info = rfc2307
        winbind enum users = yes
        winbind enum groups = yes
        server services = -dns


[netlogon]
        path = /var/lib/samba/sysvol/domain.com/scripts
        read only = No


[sysvol]
        path = /var/lib/samba/sysvol
        read only = No
        
I'm not really sure if samba is even using bind9. I've enabled the logging of bind9, but I cannot see any logs when running the dns update. Did I miss a step to activate the bind9 module?

---

### Post by rsteinmetz70112 on 2019-11-23
I'd suggest contacting the Samba mailing lists. 
They are usually quite willing to help and many of the Samba developers post there.
Many of the online guides for Samba are quite out of date.

---

### Post by SeijiSensei on 2019-11-23
> server services = -dns

Doesn't that tell Samba **not** to provide DNS?

[https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html](https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html)

---

### Post by b-david on 2019-11-23
As far as I understand this only disables the samba integrated dns server. I found this in the following guide:

[https://wiki.samba.org/index.php/Changing_the_DNS_Back_End_of_a_Samba_AD_DC](https://wiki.samba.org/index.php/Changing_the_DNS_Back_End_of_a_Samba_AD_DC)

---

### Post by SeijiSensei on 2019-11-23
What if you use that rather than BIND?

---

### Post by b-david on 2019-11-24
I've just tried that, but I'm getting the exact same errors with the internal service.

---

### Post by b-david on 2019-11-24
I was now able to solve the problem with some hints from the samba mailing list. Here is the link to the discussion: 

[https://lists.samba.org/archive/samba/2019-November/227160.html](https://lists.samba.org/archive/samba/2019-November/227160.html)

---

