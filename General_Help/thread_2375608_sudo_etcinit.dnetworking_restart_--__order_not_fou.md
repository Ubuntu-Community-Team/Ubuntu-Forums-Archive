---
title: "sudo /etc/init.d/networking restart --  order not found"
date: 2017-10-25
forum: General Help
---

### Post by jhonk on 2017-10-25
Hello People,

I have a problem when restart the network service on Ubuntu 17.10
 
sudo /etc/init.d/networking restart 

sudo /etc/init.d/networking : order not found

Help me please :(

---

### Post by Kirboosy on 2017-10-26
Hi jhonk, Welcome to the forums! :D

The command you will want to use is the following

```
sudo systemctl restart network-manager.service
```
or
```
sudo systemctl restrat network-online.target
```

---

