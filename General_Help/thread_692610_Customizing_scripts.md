---
title: "Customizing scripts"
date: 2008-02-09
forum: General Help
---

### Post by thefatmoop on 2008-02-09
So i want to make a script that will allow me to put whatever i want for a mac address and ask me what mac i want to use

#! /bin/bash
/etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sleep 4
/etc/dbus-1/event.d/25NetworkManager stop
sleep 4 
macchanger --mac="variable" eth1
sleep 4 
/etc/dbus-1/event.d/26NetworkManagerDispatcher start
sleep 4
/etc/dbus-1/event.d/25NetworkManager start
exit


the "variable" is the part that i want it to ask what i want

---

### Post by thefatmoop on 2008-02-10
bump

---

### Post by yabbadabbadont on 2008-02-10
```
echo -n "Enter MAC address: "
read variable
macchanger --mac="${variable}" eth1
```

---

### Post by thefatmoop on 2008-02-10
thank you very much just what i was looking for

---

### Post by thefatmoop on 2008-02-10
damn yeah that's perfect lol

---

