---
title: "Can't remove item from synaptic package manager"
date: 2013-04-14
forum: General Help
---

### Post by vader914 on 2013-04-14
I am using Lubuntu 12.10 and I installed zabbix-agent and now I can't remove it. I tried to re-install it but nothing is working.:([ATTACH=CONFIG]241342[/ATTACH]

---

### Post by cwsnyder on 2013-04-14
Have you tried the terminal commands? ```
apt-get purge zabbix*
```
You could also try removing or re-installing from the Ubuntu Software Center.

I assume from the application that you have at least one server on which you have installed the zabbix server component?

---

### Post by ibjsb4 on 2013-04-14
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo dpkg -r zabbix-agent
```

---

### Post by vader914 on 2013-04-14
Nope, none of that worked out. I attached what is said

---

