---
title: "How can I change log file computer name from &quot;localhost&quot; to the real name?"
date: 2007-04-11
forum: General Help
---

### Post by jelevin on 2007-04-11
I did something to my new edgy servere configuration and now the log files no longer show the computer name but show "localhost".  For example:

```
Apr 11 06:58:31 localhost dhclient: bound to 192.168.1.245 -- renewal in 19071 seconds.
```

Could some helpful person explain how the server knows its own name for the log file?  I have a different machine that is the DNS server and there is no other problems finding this new server by name.  Thanks.

---

### Post by peterbengtsson on 2007-04-11
Perhaps you need to change /etc/hosts so that it says
127.0.0.1 mycomputername

instead of 
127.0.0.1 localhost

But I'm not certain if this is where it matters but harmless to test.

---

### Post by bvucinic on 2007-04-11
If you use gnome, go to:
    System > Administration > Network
this will open a Network Settings dialog in which click on:
 General
tab, and enter your Host name.
Hope this helps.

---

