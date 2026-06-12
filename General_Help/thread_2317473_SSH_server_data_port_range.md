---
title: "SSH server data port range"
date: 2016-03-16
forum: General Help
---

### Post by joker535 on 2016-03-16
I use a ubuntu 14.04LTS instance as an SSH tunnel for multiple users. When the users establish the connections it assigns them a data port that is sometimes above 52000. A certain local ISP has issues with any traffi on ports above 52000 so I am looking for a setting to tell SSH to use ports below 52000. I looked in the SSH config file but did not see anything. Anyone know of a simple way to do this? 

Thanks

---

### Post by joker535 on 2016-03-16
**Is this a valid solution?**

Edit net.ipv4.ip_local_port_range in /etc/sysctl.conf with:

sudo vim /etc/sysctl.conf

or any other editor of your choice and add or change:

# Allowed local port range
net.ipv4.ip_local_port_range = 1024 52000

Restart your network.

**Seems to work in testing but is there any downside?**

---

