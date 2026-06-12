---
title: "SNMP error help, Error building ASN.1 representation"
date: 2019-10-02
forum: General Help
---

### Post by Drenriza on 2019-10-02
Hi all

I am trying to connect to a SNMP service that i have activated on a Synology DiskStorage.
I have activated the service with SNMP version 3, username, password and no SNMP privacy password.

I have installed the packages
```
sudo apt-get install snmp snmpd
```
On my desktop from where i would like to extract SNMP data to.

When i try to retrieve data from the SNMP Synology service i get the following error
> 
snmp_build: unknown failure
snmpget: Error building ASN.1 representation (Can't build OID for variable)


I have searched for a few hours now on what would cause this error, but i cannot find a straight answer.
My command is as follows

```

snmpget -v 3 -l authNoPriv -u USERNAME -a MD5 -A "PASSWORD" IPAddress .5.1

```

The OID of .5.1 is as Synology writes in their documentation
> Model name of the NAS

Any and all advice is most welcome!

Thanks in advance
Best regards.

---

