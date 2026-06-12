---
title: "x11vnc - Allowed connections from localhost and ......?"
date: 2008-01-11
forum: General Help
---

### Post by phillips321 on 2008-01-11
Hi guys,

I currently connect to my vnc server machine from 2 IPs, 127.0.0.1 and 192.168.1.108.

I know i can add "localhost" to the .x11vncrc file but that will limit my connections to only allow 127.0.0.1, i also need to allow connections from 192.168.1.108 (or preferable 192.168.1.xxx).

How would i go about doing this?

Does the .x11vncrc file allow this?

Many thanks

---

### Post by krunge on 2008-01-11
> **phillips321 said:**
> Hi guys,

I currently connect to my vnc server machine from 2 IPs, 127.0.0.1 and 192.168.1.108.

I know i can add "localhost" to the .x11vncrc file but that will limit my connections to only allow 127.0.0.1, i also need to allow connections from 192.168.1.108 (or preferable 192.168.1.xxx).


I think these will work:
```
-allow 127.0.0.1,192.168.1.108
```
```
-allow 127.0.0.1,192.168.1.
```
either from the command line or ~/.x11vncrc file.  I.e. a comma separated list of IP's or hostnames. 192.168.1. acts as a wildcard.

---

### Post by phillips321 on 2008-01-12
magic, i guess "196.168.1." allows the full /24 subnet?

Guess this solves my problem, many thanks for your help

---

### Post by krunge on 2008-01-13
> **phillips321 said:**
> magic, i guess "196.168.1." allows the full /24 subnet?

Yes, it is just a simple beginning of string match for the IP addr considered as a string.  "192.168.1" would also match IPs in the 10 and 100 blocks, so best to include the trailing dot.

---

