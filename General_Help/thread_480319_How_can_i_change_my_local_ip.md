---
title: "How can i change my local ip?"
date: 2007-06-21
forum: General Help
---

### Post by Erdem on 2007-06-21
hey
i'm using ubuntu 7.04 server edition... and i dont have x on server pc...
my router give me ip 192.168.1.25 but i need to change that 192.168.1.100 (its local ip)

how can i do that?

thanks for helping...

---

### Post by harty83 on 2007-06-21
Open and edit your interfaces file
```
sudo pico /etc/network/interfaces
```

Change your interface to (make sure you change eth2 to your interface)
```

iface eth2 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

```

Press ctrl-o to save then ctrl-x to exit.

Then restart networking

```
sudo /etc/init.d/networking restart
```

Check your connection.

---

### Post by Erdem on 2007-06-22
thank u so much :)

---

