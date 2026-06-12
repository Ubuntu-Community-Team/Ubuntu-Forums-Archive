---
title: "Problems connecting externally from Zend - java issue?"
date: 2008-04-28
forum: General Help
---

### Post by eludlow on 2008-04-28
Upgraded from Gutsy to Heron over the weekend, and this morning launched Zend Studio for the first time (Monday morning..back to work!) but for some reason it wouldn't connect to any of my external FTP servers BUT it would connect fine to my FTP server running on the same box (ie localhost).

Didn't think of anything of it at the time and used another PC but now I've come back to it to try and work out what's going on...it STILL won't connect to anything externally from Zend - if I do a "check for updates" it tells me a connection to Zend auto-update couldn't be established.

Connecting to FTP servers from Filezilla works fine, from the terminal works fine - so I'm stumped.  Is it possibly connections from java apps being blocked?

Any advice appreciated.

Thanks,
Ed Ludlow

---

### Post by eludlow on 2008-04-29
Shameless bump :oops:

---

### Post by bdevild on 2008-04-29
I fixed my java network connectivity issues by blacklisting ipv6/net-pf-10 as per:


```

sudo vi /etc/modprobe.d/blacklist

```
and added:
```

blacklist net-pf-10
blacklist ipv6

```

see 
[http://ubuntuforums.org/showthread.php?t=772396](http://ubuntuforums.org/showthread.php?t=772396)

---

### Post by eludlow on 2008-04-29
Marvellous - it's worked!  Thank you so much.

---

