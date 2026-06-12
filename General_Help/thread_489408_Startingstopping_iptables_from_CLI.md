---
title: "Starting/stopping iptables from CLI"
date: 2007-07-01
forum: General Help
---

### Post by bowens44 on 2007-07-01
How can I start/stop/restart iptables from the CLI? I have tried sudo /etc/init.d/iptables stop' etc  but get the following error 'sudo: /etc/init.d/iptables: command not found'.

Alsao, although it is running I don't see it as a service when I go to system settings/system services.

---

### Post by McNils on 2007-07-01
You can delete all rules with ```
sudo iptables -F
```

---

### Post by pxwpxw on 2007-07-01
You dont stop and start that way. See man iptables, The (easy) way I do it is by installing firestarter, which you can use to start/stop from CLI, using /etc/init.d/firestarter. The process involves loading and unloading iptables filters, best understood by looking at the firestarter scripts.

---

### Post by bowens44 on 2007-07-01
> **McNils said:**
> You can delete all rules with ```
sudo iptables -F
```

I realize that but that's not what I want to do. I want to be able to stop, start and restart the service from the command line  like I can in other distributions.

---

### Post by bodhi.zazen on 2007-07-01
See this page : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

At the bottom is a script to be able to do as you ask.

(Direct : [http://doc.gwos.org/index.php/IptablesFirewall#The_scripts](http://doc.gwos.org/index.php/IptablesFirewall#The_scripts))

---

