---
title: "firehol blocking too much"
date: 2006-07-07
forum: General Help
---

### Post by shanepardue on 2006-07-07
i am using firehol along with dansguardian and tinyproxy for a web filter. i've got everything in place as far as the filter. firehol makes it so even as a direct connection in firefox, the web still goes through the proxy. my only problem is that firehol is also blocking my gdesklets and the network's samba shares.

just some background..we're running dhcp with multiple computers.

here's my firehol.conf

```
[SIZE="4"]iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept[/SIZE]
```

---

### Post by vem0m on 2006-07-08
so is this anything like a multi-firewall setup? as i dunno about linux but u try and use more then one firewall in windows it fails and either blocks everything or they fight with each other as it seems to be doing here

---

### Post by shanepardue on 2006-07-08
not exactly sure what you are talking about, but i only have one firewall set up at the moment..firehol alone and my code was included in my previous post.

---

### Post by vem0m on 2006-07-08
well u are talking about multi ip blockers which is a form of a firewall on windows u run more then one it usally starts to either block wrong things or block each other and fight over the system i dunno how it is in windows but that is what it sounds like

---

### Post by shanepardue on 2006-07-08
ok, so with a dhcp network, how would i go about allowing certain ip addresses? i don't even know how to include/exclude ip addresses with firehol...also, is it possible to allow certain ip addresses for sharing on a dhcp network?

---

### Post by shanepardue on 2006-07-08
i don't even really need a software firewall, but i set one up to enable this transparent proxy..is there a way to allow all connections with it?

---

### Post by shanepardue on 2006-07-10
still can't access gdesklets and samba shares with firehol enabled. please see above for conf. i need help! hehe

---

### Post by tonhou on 2006-07-10
Not sure about gdesklets, but for samba try adding:

server samba accept

You might like to have a look at the commands at:

[http://firehol.sourceforge.net/commands.html](http://firehol.sourceforge.net/commands.html)

I put up the howto on dansguardian on a single desktop that I think you have followed.

--Tony

Here is a better page:

[http://firehol.sourceforge.net/services.html](http://firehol.sourceforge.net/services.html)

---

### Post by shanepardue on 2006-07-10
i'm not near the network that was having this issue, but wouldn't CLIENT ALL ACCEPT take care of samba shares?

and thank you very much for your help! those commands will come in handy.

---

