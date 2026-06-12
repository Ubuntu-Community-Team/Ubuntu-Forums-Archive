---
title: "Is it possible to do a ping function with ubuntu?"
date: 2007-09-16
forum: General Help
---

### Post by Petrock6 on 2007-09-16
Is it possible to in bash or whatever to do a ping command?

---

### Post by kevdog on 2007-09-16
Yes

ping <name or ipaddress>

---

### Post by expatCM on 2007-09-16
Think you can also enable "Network Tools" which will be in the menu of System / Administration.  This gives you not only Ping but also a range of tools including TraceRoute, Lookup, Finger, Port Scan, Whois ....

---

### Post by mojoman on 2007-09-16
> **Petrock6 said:**
> Is it possible to in bash or whatever to do a ping command?

I prefer to do 
```

ping -c # IP.ADDRESS.TO.TARGET
```

substitute # for the number of pings you want it to send. The default is to keep trying until interupted so I like to set a limited number of times. Something I learned after I accidently left my computer to do a ping all night on a friends IP...

---

### Post by nonewmsgs on 2007-09-16
> **mojoman said:**
> I prefer to do 
```

ping -c # IP.ADDRESS.TO.TARGET
```

substitute # for the number of pings you want it to send. The default is to keep trying until interupted so I like to set a limited number of times. Something I learned after I accidently left my computer to do a ping all night on a friends IP...

that's the redneck version of a DOS attack.

---

### Post by mojoman on 2007-09-16
> **nonewmsgs said:**
> that's the redneck version of a DOS attack.

Hehe, yeah, I know. Though the pings are not frequent enough to do any real harm it's still better to use a limited amount of pings, just in case you do forget about it. In this case I noticed it next morning and my friend hadn't noticed at all. :lolflag:

---

### Post by HermanAB on 2007-09-16
You may find 'traceroute' better for diagnosing problems, than 'ping'.

Cheers,

H.

---

