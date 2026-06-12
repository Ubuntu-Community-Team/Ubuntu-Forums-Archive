---
title: "Ubuntu (Debian) server networking, logs"
date: 2008-04-01
forum: General Help
---

### Post by artfwo on 2008-04-01
You should edit the file **/etc/network/interfaces** like this:

I suppose, your server IP is 192.168.1.1

```
iface eth0 inet static
  address 192.168.1.1
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255
```

And that's it! On reboot you'll always get the address from **interfaces** and never get bothered by DHCP ;)

---

