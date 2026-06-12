---
title: "port 500 in use, how to clear it?"
date: 2006-10-08
forum: General Help
---

### Post by Boomy on 2006-10-08
How can I find out what process is using port 500? I'm trying to tunnel a vpn, but I keep getting "address is in use, port 500"

---

### Post by bikeboy on 2006-10-08
I'm no guru but try:```
netstat -a | grep tcp
```

---

### Post by moma on 2006-10-08
This manual may also help
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-server-ports.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-server-ports.html)

---

