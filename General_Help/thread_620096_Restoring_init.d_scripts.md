---
title: "Restoring init.d scripts"
date: 2007-11-22
forum: General Help
---

### Post by lukebaldan on 2007-11-22
Hi guys,
I've been mucking around with snmp and have accidentally deleted the /etc/init.d/snmpd startup script. How can i get it back? Re-installing snmp does not restore the script.

Thanks, Luke

---

### Post by misconfiguration on 2007-11-23
Your best bet is to find the plain-text init script on the net. Then do the following:
```

touch /etc/rc.d/init.d/snmpd
```

```
vi /etc/rc.d/init.d/snmpd ( or your favorite editor)
```

paste the init script in this file.

```
chmod 755 /etc/rc.d/init.d/snmpd
```

---

### Post by chrisccoulson on 2007-11-23
> **lukebaldan said:**
> Hi guys,
I've been mucking around with snmp and have accidentally deleted the /etc/init.d/snmpd startup script. How can i get it back? Re-installing snmp does not restore the script.

Thanks, Luke

Did you try re-installing the package snmp or snmpd? You need to reinstall snmpd

---

