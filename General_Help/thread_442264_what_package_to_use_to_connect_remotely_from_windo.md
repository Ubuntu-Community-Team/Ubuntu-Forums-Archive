---
title: "what package to use to connect remotely from windows towards ubuntu?"
date: 2007-05-13
forum: General Help
---

### Post by paulus4605 on 2007-05-13
Dear,
since I'm new to ubuntu I would like to have a possibility to establish a remote connection from my windows pc to my linux pc which soft is the best to use
thanks for your reaction.

---

### Post by taurus on 2007-05-13
You need to install sshd on your Ubuntu first before you can connect to it from anywhere on the net.

```
sudo aptitude update
sudo aptitude install openssh-server
```

And if your machine is connected to a router, then you need to go into your router and open port 22 for incoming signal.

---

