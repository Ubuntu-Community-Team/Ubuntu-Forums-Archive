---
title: "upstart - how to check is openvpn is connected?"
date: 2013-03-14
forum: General Help
---

### Post by josephonthejob on 2013-03-14
Hi,

I need to run a script after mysql and ovpn has started.
This could be done very easily with upstart, I do that with this script in /etc/init/

```
start on (starting openvpn and started mysql)


  script cd /home/ubuntu/developedGZ/provaMySql/ 
./provaMySql 
end script


```

The script succesfully run after mysql but not after openvpn connected.
How can I do that?

Thank you
regards

Giuseppe

---

### Post by josephonthejob on 2013-03-15
I solved this in a very simple manner:
I changed my start on condition in:

```
start on (started mysql and net-device-added INTERFACE=tun0)
```

and works very well!..for now..

---

### Post by meiskam on 2013-06-16
> **josephonthejob said:**
> I solved this in a very simple manner: I changed my start on condition in:  ```
start on (started mysql and net-device-added INTERFACE=tun0)
```  and works very well!..for now..  Thank you so much, I was trying: ```
net-device-up IFACE=tun0
``` and it was failing, because the device didn't exist when checked.

---

