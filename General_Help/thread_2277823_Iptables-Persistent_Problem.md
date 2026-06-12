---
title: "Iptables-Persistent Problem"
date: 2015-05-11
forum: General Help
---

### Post by mark120 on 2015-05-11
Hi,


I have tried to implement the following rule into iptables-persistent:


-A INPUT -p tcp -m state --state NEW -s <start ip> -d <end ip> --dport 27199 -j ACCEPT


When i try and reload the firewall I am getting the follwing error:



/etc/init.d/iptables-persistent: 27: /etc/init.d/iptables-persistent: -A: not found




Can anybody please tell me what is wrong with my syntax, or what I need to do to resolve to error?


Thanks.

---

### Post by Doug S on 2015-05-12
Some context would  help, such as the listing for the file.
Just guessing, but it looks as though the file is some script and that it expects this:```
iptables -A INPUT -p tcp -m state --state NEW -s <start ip> -d <end ip> --dport 27199 -j ACCEPT
```

---

### Post by nerdtron on 2015-05-12
Or better yet, use the default ufw utility for this.

```
sudo ufw allow from [source ip/ipcblock] to [destination ip/ipblock] port 27199 
```

---

