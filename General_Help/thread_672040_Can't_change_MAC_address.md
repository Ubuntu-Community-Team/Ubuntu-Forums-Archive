---
title: "Can't change MAC address?"
date: 2008-01-19
forum: General Help
---

### Post by Antexter on 2008-01-19
So I can't change the mac address doing 
> sudo ifconfig xxx down
sudo ifconfig xxx hw ether xxxxxxxxxxxx
sudo ifconfig xxx up

and with macchanger it says its been changed but it it goes back to what I don't want it to be

---

### Post by tehet on 2008-01-19
I don't know why that's not working, but you can edit your /etc/network/interfaces like so:
```
iface eth0 inet dhcp
    hwaddress ether xxxxxxxxxxxx   #add this line
    netmask 255.255.0.0
    ...
```
This works for me.

---

