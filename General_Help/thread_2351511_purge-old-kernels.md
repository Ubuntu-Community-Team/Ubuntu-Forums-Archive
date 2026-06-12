---
title: "purge-old-kernels"
date: 2017-02-04
forum: General Help
---

### Post by zkab on 2017-02-04
I have 16.04.1 LTS (Xenial Xerus - 4.4.0-62-generic) desktop installed on a computer.
For some reason is 'purge-old-kernels' script not installed.

rajan@fe-sovis:~$ sudo purge-old-kernels --keep 2 -qy
sudo: purge-old-kernels: command not found
rajan@fe-sovis:~$ locate purge-old-kernels

Do I have to install it manually ?

---

### Post by howefield on 2017-02-04
Think you would have to install the byobu package to get the purge-old-kernels script in 16.04.

Alternatively use 

```
sudo apt autoremove --purge
```

Or set unattended-upgrades to do it automatically.

```
sudo nano /etc/apt/apt.conf.d/50unattended-upgrades
``` 

and set the following line to "true"

```
//Unattended-Upgrade::Remove-Unused-Dependencies "false";
```

---

### Post by zkab on 2017-02-04
Thanks ...

---

### Post by ian-weisser on 2017-02-04
Most users should not need a purge-old-kernels script in 16.04 and later.
That feature was added to unattended-upgrades (include by default) in 16.04.

---

### Post by zkab on 2017-02-04
Ok

---

