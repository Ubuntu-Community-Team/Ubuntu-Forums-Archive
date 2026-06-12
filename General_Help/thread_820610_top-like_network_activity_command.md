---
title: "top-like network activity command"
date: 2008-06-06
forum: General Help
---

### Post by agentjon on 2008-06-06
Hello:

Does anyone know of a command that shows a list of which processes are using the network, and how much?  I already know about lsof -i, which shows which ports are being used, and the processes that are using them; I also use the gnome system monitor to see spikes in network activity, but I can't seem to find anything that shows me a combination of the two.

Any suggestions?

---

### Post by spiderbatdad on 2008-06-06
check out the man pages on netstat...for example: ```
sudo netstat -catnup
```

---

### Post by Monicker on 2008-06-06
> **agentjon said:**
> Hello:

Does anyone know of a command that shows a list of which processes are using the network, and how much?  I already know about lsof -i, which shows which ports are being used, and the processes that are using them; I also use the gnome system monitor to see spikes in network activity, but I can't seem to find anything that shows me a combination of the two.

Any suggestions?

I saw this recommended in another thread not long ago.

[http://packages.ubuntu.com/hardy/nethogs](http://packages.ubuntu.com/hardy/nethogs)

---

### Post by agentjon on 2008-06-09
both of these are really useful. thanks!

---

