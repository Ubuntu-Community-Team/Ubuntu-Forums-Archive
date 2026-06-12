---
title: "host name changed  suddenly"
date: 2015-12-27
forum: General Help
---

### Post by monkeybrain20122 on 2015-12-27
I have not been doing anything with networking or messing with host files. But all of a suddenly somehow my host name has changed from localhost to 
"new-host" from the terminal's command prompt and sudo complains that it cannot resolve host new-host.  Any idea what happened and how to change it back?

Thanks.

Ubuntu 15.10 desktop.

---

### Post by monkeybrain20122 on 2015-12-27
/etc/hosts and /etc/hostname looked like these

 ```
cat /etc/hosts
127.0.0.1    localhost
127.0.1.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

```
cat /etc/hostname

localhost
```

The terminal prompt showed
```

monkeybrain@new-host
```

and the upper left corner of the login screen also showed 
```
new-host
```

If I change them to 
```
cat /etc/hosts
127.0.0.1    localhost
127.0.1.1 monkeybrain-localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

```
cat /etc/hostname

monkeybrain-localhost
```

Then it works normally again and login screen now shows localhost
and command prompt shows monkeybrain@monkeybrain-localhost


 But I don't know why this problem haven't occurred before, it just started out of the blue.

---

### Post by HermanAB on 2015-12-27
It likely has something to do with your DHCP lease renewal.  Check your DHCP server settings.

---

### Post by monkeybrain20122 on 2015-12-27
> **HermanAB said:**
> It likely has something to do with your DHCP lease renewal.  Check your DHCP server settings.

Can you explain these please? How do I check my DHCP server settings and what should I look at? Thanks.

---

