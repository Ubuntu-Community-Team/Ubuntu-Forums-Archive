---
title: "Traffic Logging"
date: 2008-05-19
forum: General Help
---

### Post by cminicooperj on 2008-05-19
I'm looking for a program.  I want one that will log all the internet traffic information that passes through my computer.  I just want to know things like the time, date, IP address that it's going to, whether it is ingoing or outgoing, and the port.  I know this is detailed, but even a program that can only do some of this would be great.  If anyone has ever used sygate personal firewall on windows, that is the exact type of logging that I would like on Ubuntu. Thanks ahead of time :D

---

### Post by HalPomeranz on 2008-05-19
Linux has a firewall called IP Tables built into the kernel, though Ubuntu disables it by default.  If all you want to do is log packets passing in and out of your system, just run the following commands:

```
sudo iptables -A INPUT -j LOG
sudo iptables -A OUTPUT -j LOG
sudo iptables -A FORWARD -j LOG
```

Or, if you want to make sure this always happens when you reboot, just put three similar lines in your /etc/rc.local:

```
iptables -A INPUT -j LOG
iptables -A OUTPUT -j LOG
iptables -A FORWARD -j LOG
```

Notice you don't need the "sudo" commands because rc.local will be executed with root privs at boot time.

Logs end up in /var/logs/kern.log.

---

