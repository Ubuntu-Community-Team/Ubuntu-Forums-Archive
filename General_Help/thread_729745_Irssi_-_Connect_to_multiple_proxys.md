---
title: "Irssi - Connect to multiple proxys"
date: 2008-03-20
forum: General Help
---

### Post by Ballena on 2008-03-20
Hi


I have recently started using Irssi as my primary IRC-client and I'm very satisfied. The irssi-proxy is very handy but there is one poblem. I can connect to this irssi-proxy on my computer1 from almost any client but the problem is that you have to make a separte connection to a different port on computer1 to each IRC-server you want to connect to. This works fine in most GUI-IRC-clients I have tried but how do you do this in Irssi on compuer2? 


The official [Startup-HOWTO]("http://irssi.org/documentation/startup") says you should do the following:


```
/SET use_proxy ON
/SET proxy_address irc.bouncer.org
/SET proxy_port 5000

/SET proxy_password YOUR_BNC_PASSWORD_HERE
/SET -clear proxy_string
/SET proxy_string_after conn %s %d
```

And this works - but only for **one** connection :( I want to connect to all my connections on the computer1's irssi-proxy.


Is there a way to make this? Any help is much appreciated.
/Ballena

---

### Post by Ballena on 2008-03-21
Noone knows? :(

---

