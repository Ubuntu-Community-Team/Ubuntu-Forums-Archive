---
title: "Ethernet connection disconnect randomly"
date: 2018-12-09
forum: General Help
---

### Post by corradoventu on 2018-12-09
Ethernet connection id dropped randomly, sometimes works fine for the whole day, sometimes the connection falls 2 or 3 times i a hour
I have the problem with Ubuntu 18.10 with standard kernel and with 19.04 with standard (4.18.0-11) and with 4.20.0-042000rc4 mainline kernel.
When the connection drops i can restart it just closing and restarting the net.
```
corrado@corrado-p3-cosmic:~$ inxi -Nx
Network:
  Device-1: Intel Ethernet I219-V driver: e1000e v: 3.2.6-k port: N/A 
  bus ID: 00:1f.6 
corrado@corrado-p3-cosmic:~$ 

```I found a bug for the same? problem but has incomplete info: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1785171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1785171)
so i opened a new bug: [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1806458](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1806458) hoping to give more info.
can anyone suggest what i should look for on syslog? or what tests do?
thanks

---

