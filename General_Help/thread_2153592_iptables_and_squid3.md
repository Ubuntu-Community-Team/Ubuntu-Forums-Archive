---
title: "iptables and squid3"
date: 2013-06-11
forum: General Help
---

### Post by Dagaroth on 2013-06-11
i have a working transparent proxy trying to figure a few things with iptables though.

i had added my own rules via terminal and saved them with the save, restore options.

then i went to edit them again with gedit and it added some of its own to the file.

here's what it added.....

```

-A FORWARD -d 10.42.0.0/24 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -s 10.42.0.0/24 -i eth1 -j ACCEPT
-A FORWARD -i eth1 -o eth1 -j ACCEPT
-A FORWARD -o eth1 -j REJECT --reject-with icmp-port-unreachable
-A FORWARD -i eth1 -j REJECT --reject-with icmp-port-unreachable

-A POSTROUTING -s 10.42.0.0/24 ! -d 10.42.0.0/24 -j MASQUERADE

```

this is what i added when i edited the file.

```

-A FORWARD -i eth0 -o eth1 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i eth1 -o eth0 -j ACCEPT
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
-A POSTROUTING -o eth0 -j MASQUERADE

```

which should i use i've always used the bottom and worked well.
if anyone could clarify the upper portion would be great....
i'm curious as why it added it own with mine though :D

---

### Post by Dagaroth on 2013-06-13
any1 hehe

---

### Post by HiImTye on 2013-06-13
since the rules are for IPs in the 10.x.x.x range, I would assume they are for some sort of virtual network - a VPN, or VirtualBox, perhaps?
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Dagaroth on 2013-06-13
nope it's the subnet for the lan :D
just don't get why it tried to add it's own rules after i had put my own in there lol.
the bottom portion of the code is what i've always used for the nat and the proxy.

---

### Post by SeijiSensei on 2013-06-13
I still don't know what you mean by "it."  In your original post the referent of "it" is "gedit."  I'm sure that's not what you mean.

---

### Post by Dagaroth on 2013-06-13
yah, when i opened iptables.rules with gedit it tried to add the top portion of rules i posted after i saved mine to the iptables.rules.

---

