---
title: "VNC &amp; SSH Chain tunnelling"
date: 2012-11-07
forum: General Help
---

### Post by MadsRC on 2012-11-07
Here's the scenario
2 servers:
[LIST]
[*]Serv01 - VNC & SSH
[*]Serv02 - SSH
[/LIST]
In my firewall I've mapped outside port 8542 to Serv01 port 5901 and outside port 22 to Serv02 port 22.

I'd like to, from WAN to use a SSH tunnel to connect to VNC on Serv01, possibly without opening it to the world via SSH (IE: Don't open another port)

Is this possible? If so, how?

I know a regular SSH tunel is:
```
ssh user@domain -L 5901/127.0.0.1/5901
```
But I can't seem to adapt that to the above setup (Even if I open up for SSH from WAN to Serv01).

---

### Post by Lars Noodén on 2012-11-07
You can get to machine2 via machine1 this way:

```

ssh -L 5901:machine2.example.org:5901 machine1.example.org

```

Then just connect to port 5901 on the local host and you're connected to machine2.  It's doable with keys, too.

---

### Post by dannyboy79 on 2012-11-07
lars beat me to it.

---

