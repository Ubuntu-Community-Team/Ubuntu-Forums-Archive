---
title: "Computer refuses to shut down: it just sits there"
date: 2008-04-27
forum: General Help
---

### Post by agentnixon on 2008-04-27
Hi, I've upgrraded to Hardy, and now my computer refuses to shutdown or sleep whenever I tell it to in the UI or even in the terminal. It just sits there...

However, when I hit the power button to hard reset, it turns off, but not before giving me a slew of error messages regarding the network manager. 

I am in a pretty much fresh install of 8.04 with a few things installed such as flash plugin and wine.

---

### Post by ghost_ryder35 on 2008-04-27
you should do it in the terminal and type
 
```

sudo halt

```
 
then let us know what Network Manager is complaining about

---

### Post by agentnixon on 2008-04-27
Apparently, the terminal shuts down works now, but it still gives me a slew of messages including a warning about "make sure the message bus daemon is running" and something with network manager and dbus. It went by so fast that it was hard to catch everything. Is there a log file that I could read?

Shutting down/restarting from the UI still doesn't work though.

---

