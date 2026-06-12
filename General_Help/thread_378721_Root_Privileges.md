---
title: "Root Privileges"
date: 2007-03-07
forum: General Help
---

### Post by ComputerGuy56 on 2007-03-07
I'm trying to use IP Tables to do some stuff but whatever i do it comes up with this message:
iptables v1.3.5: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
I typed iptables --list
I tried to put my Username in the root user group but the same thing happend. And somewhere it said to never log in via root.

---

### Post by invalid on 2007-03-07
```
sudo <app>
``` runs an application as root.

---

### Post by bodhi.zazen on 2007-03-07
You can ```
sudo -i
``` to become root

And then there's the classics :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by ComputerGuy56 on 2007-03-07
Alright I will try those things.

---

