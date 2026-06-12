---
title: "[SOLVED] kdesu kate /etc/dhcp3/dhclient.conf  help"
date: 2007-10-06
forum: General Help
---

### Post by r4ik on 2007-10-06
In gnome when i do a sudo gedit /etc/dhcp3/dhclient.conf i can change my prepend domain-name-servers.
In KDE a kdesu kate /etc/dhcp3/dhclient.conf  gives me a more or less empty file.
Anyone with a pointer please ?

---

### Post by por100pre1 on 2007-10-06
Weird, that should work. Check if kedit has the same beahvior: :-k

```
kdesu kedit /etc/dhcp3/dhclient.conf
```

Could it be issue with your KDE color settings?

---

### Post by r4ik on 2007-10-06
That worked thanks, as a KDE noob i am not going to question the reason at the moment.
Thanks for you&#341;e help !

---

