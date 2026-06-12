---
title: "Sudo Error!"
date: 2006-08-06
forum: General Help
---

### Post by zxcvbnm on 2006-08-06
Hi, I just changed my hostname, And now I get the getbyhostname error whenever I use sudo.

Here are my logs:

/etc/hosts
```

127.0.0.1 localhost Ubuntu 
127.0.1.1 Ubuntu 

# The following lines are desirable for IPv6 capable hosts ::1 ip6-localhost 
ip6-loopback fe00::0 
ip6-localnet ff00::0 
ip6-mcastprefix ff02::1 
ip6-allnodes ff02::2 
ip6-allrouters ff02::3 
ip6-allhosts
```


/etc/hostame
```
Ubuntu
```

-thanks

---

### Post by vijirajan on 2006-08-06
To change your host name just swap localhost and Ubuntu in the first line of your /etc/hosts file as in
```

127.0.0.1 Ubuntu localhost

```

The line following that has to be removed. That is the culprit thats causing gethostbyname error.

```

127.0.1.1 Ubuntu

```

---

