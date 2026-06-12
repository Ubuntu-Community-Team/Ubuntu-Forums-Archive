---
title: "Problem with /etc/security/limits.conf"
date: 2008-02-06
forum: General Help
---

### Post by bodyn on 2008-02-06
I have Ubuntu Server 7.10
File /etc/security/limits.conf is

#<domain>      <type>  <item>         <value>

*                soft    nofile          2048 
*                hard    nofile         2048 


I reboot machine and login 
#ulimit -a returns
1024. 
Why not 2048?

---

### Post by pointone on 2008-02-06
What happens if you actually try to set your nofile limit above 2048?

```
ulimit -n 2049
```

---

