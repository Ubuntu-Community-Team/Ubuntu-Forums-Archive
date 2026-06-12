---
title: "Questions about ufw"
date: 2008-05-15
forum: General Help
---

### Post by _sAm_ on 2008-05-15
Hi – I am trying to learn how to use the new firewall ufw, and have some questions. 

I know how to turn of and on one and one port with ufw, but how can you turn on several at the same time. I use Deluge for bit torrent, and it use random ports from 6881 to 6889 – how can I open these ports(or Deluge as a service)?

And second, when you open Nautilus it can browse folders on your LAN(like samba shares). What is this called, right now ufw has closed it down and I don't know what to open. 

Thanks for any help:-)

---

### Post by bodhi.zazen on 2008-05-15
I have not tried it yet, but I believe you can add your services / ports to 

/etc/services

Or you can allow one port at at time (or write a script)

See : [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

For samba, to you local net, assuming a net mask of 192.168.0.1/24 ...

Allow samba :

```
sudo ufw allow proto tcp from 192.168.1.0/24 to 192.168.1.0/24 port 135
sudo ufw allow proto udp from 192.168.1.0/24 to 192.168.1.0/24 port 137
sudo ufw allow proto udp from 192.168.1.0/24 to 192.168.1.0/24 port 138
sudo ufw allow proto tcp from 192.168.1.0/24 to 192.168.1.0/24 port 139
sudo ufw allow proto tcp from 192.168.1.0/24 to 192.168.1.0/24 port 445
```Allows samba on the LAN 192.168.0.1/24

---

### Post by jrave on 2010-11-06
sudo ufw allow 6881:6999/tcp

sudo ufw allow 6881:6999/udp

---

