---
title: "Can't boot after installing nvidia drivers"
date: 2012-10-21
forum: General Help
---

### Post by nedimBosnia on 2012-10-21
Ok i've installed nvidia drivers on my ubuntu desktop 12.04 and after restarting I get purple ubuntu loading screen then redirecting me to tty1 

-Sorry for bad English

---

### Post by timgood on 2012-10-21
This is a known bug. You need to uninstall the drivers and then

```
sudo apt-get install linux-headers-generic
```

then re-install the drivers. 

Hope this helps.

---

### Post by nedimBosnia on 2012-10-21
> **timgood said:**
> This is a known bug. You need to uninstall the drivers and then

```
sudo apt-get install linux-headers-generic
```

then re-install the drivers. 

Hope this helps.

How to uninstall drivers, sorry but im newbie

atm im just able to use tty1 screen ...

---

### Post by nedimBosnia on 2012-10-21
any help ?? please

---

### Post by flyboy on 2012-10-21
Remove your nvidia drivers with:
```
sudo apt-get remove nvidia-current
```
(assuming the nvidia-current drivers were selected).

Then follow the instructions above to install the headers, and to reinstall the nvidia drivers:
```
sudo apt-get add nvidia-current
```

---

