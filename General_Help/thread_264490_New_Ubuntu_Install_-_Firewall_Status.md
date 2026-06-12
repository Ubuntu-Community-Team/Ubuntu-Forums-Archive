---
title: "New Ubuntu Install - Firewall Status?"
date: 2006-09-24
forum: General Help
---

### Post by mac57 on 2006-09-24
I have just installed Ubuntu 6.06 Dapper Drake. I am new to both Ubuntu and to Gnome, but certainly not new to Linux, having used it for years.

With this new Ubuntu install, is there some default firewall set up, or do I need to install one from one of the repositories? If there is a firewall setup, where do I go to find its settings and adjust it? As a simple example, if I start the purftpd FTP daemon, I need to be able to open port 21. Where do I do such a thing?

Thanks!

---

### Post by lamego on 2006-09-24
There is no firewall as default, also there are no services with open ports (as default).

Update: I meant there are no firewall rules setup, iptables is installed.

---

### Post by Omnios on 2006-09-24
Ubuntu has iptables as a back end. The most popular firewall front end is Firestarter available from Synaptic repository which allows for rules.

---

### Post by reacocard on 2006-09-24
There is no firewall by default. guarddog is a good choice for a firewall, and it's in the repos. just

```
sudo apt-get install guarddog
```

firestarter is another good choice, but it's not as configurable. both are frontends to iptables.

---

### Post by mac57 on 2006-09-24
Thanks, sorry for what seems like such a stupid question

---

