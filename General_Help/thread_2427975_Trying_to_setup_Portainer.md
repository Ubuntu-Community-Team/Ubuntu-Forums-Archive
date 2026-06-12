---
title: "Trying to setup Portainer"
date: 2019-09-28
forum: General Help
---

### Post by billybaldin on 2019-09-28
Anyone have any thoughts on what I am missing here?
I have made it this far and can't figure this one out. 
Thank you
```
bill@BillsUBU:~$     command: -H unix:///var/run/docker.sock
command:: command not found
bill@BillsUBU:~$     ports:
ports:: command not found
bill@BillsUBU:~$       - "XXXX:9000"
-: command not found
bill@BillsUBU:~$     volumes:
volumes:: command not found
bill@BillsUBU:~$       - /var/run/docker.sock:/var/run/docker.sock
-: command not found
bill@BillsUBU:~$       - ${USERDIR}/docker/portainer/data:/data
-: command not found
bill@BillsUBU:~$       - ${USERDIR}/docker/shared:/shared
-: command not found
bill@BillsUBU:~$     environment:
environment:: command not found
bill@BillsUBU:~$       - TZ=${TZ}
-: command not found
bill@BillsUBU:~$ docker-compose -f ~/docker/docker-compose.yml up -d
ERROR: In file '/home/bill/docker/docker-compose.yml', service must be a mapping, not a NoneType.
bill@BillsUBU:~$
```

---

