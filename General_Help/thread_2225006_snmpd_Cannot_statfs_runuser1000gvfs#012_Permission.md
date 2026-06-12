---
title: "snmpd Cannot statfs /run/user/1000/gvfs#012: Permission denied"
date: 2014-05-19
forum: General Help
---

### Post by juju43 on 2014-05-19
Hello,

I setup snmpd on a lubuntu 14.04 

in my snmpd.conf, have (default)
```

disk       /     10000
disk       /var  5%
includeAllDisks  10%
```

but I got my /var/log/syslog polluted by

```

May 19 10:50:03 my-computer snmpd[2690]: Cannot statfs /run/user/1000/gvfs#012: Permission denied
May 19 10:50:03 my-computer snmpd[2690]: Cannot statfs /home/my-user/.gvfs#012: Permission denied
May 19 10:50:03 my-computer snmpd[2690]: Cannot statfs /run/user/1000/gvfs#012: Permission denied
May 19 10:50:03 my-computer snmpd[2690]: Cannot statfs /home/my-user/.gvfs#012: Permission denied
May 19 10:55:03 my-computer snmpd[2690]: Cannot statfs /run/user/1000/gvfs#012: Permission denied
May 19 10:55:03 my-computer snmpd[2690]: Cannot statfs /home/my-user/.gvfs#012: Permission denied
May 19 10:55:03 my-computer snmpd[2690]: Cannot statfs /run/user/1000/gvfs#012: Permission denied
May 19 10:55:03 my-computer snmpd[2690]: Cannot statfs /home/my-user/.gvfs#012: Permission denied

```

I remove includeAllDisk to list each real partition but I still got those.

Any way to avoid this pollution ?

Thanks

---

