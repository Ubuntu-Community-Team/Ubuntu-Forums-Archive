---
title: "MySQL &quot;Lost connection&quot; over network"
date: 2007-10-18
forum: General Help
---

### Post by palmnut on 2007-10-18
Banging my head on this one:

I have a problem accessing MySQL over my home network. I have a server running Gutsy which has a MySQL database on it. From a terminal on that server I can enter:

```
mysqladmin -u user -p variables
```

and get the proper output.

I can also enter:

```
mysqladmin -h 192.168.2.55 -u user -p variables
```

where 192.168.2.55 is the ip address of the server - I get the right output

But when I try exactly this same command over the network I get:

> mysqladmin: connect to server at '192.168.2.55' failed
error: 'Lost connection to MySQL server during query'

I have commented out bind = 127.0.0.1 in the my.cnf file on the server (and on the machine from which I'm trying to access it). User 'user' is defined for host % on the server.

Help please?

---

