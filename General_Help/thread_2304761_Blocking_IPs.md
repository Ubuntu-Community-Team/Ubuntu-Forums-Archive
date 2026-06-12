---
title: "Blocking IPs"
date: 2015-11-29
forum: General Help
---

### Post by shane_faulkinbury2 on 2015-11-29
I just have a general question about blocking IPs. Is there anyway of blocking an IP that I find running a netstat -ntu | awk '/ESTABLISHED/{print $5;}' in Terminal?  I was just wanting to know because I really want to block Akamai's range of IPs from 23.192.0.0 - 23.223.255.255 !

---

### Post by The Cog on 2015-11-29
This command does it, blocking the entire range:
```
sudo iptables -I INPUT -s 23.192.0.0/11 -j DROP
```
You can add the command (without the sudo prefix) to /etc/rc.local so it runs on every boot.

---

### Post by shane_faulkinbury2 on 2015-11-29
Thanks!  Much appreciated Cog!  :D

In etc/rc.local how do you save?  The save button never highlights!

---

### Post by The Cog on 2015-11-29
You need to edit it with root privilege. Try this command:
```
sudo nano /etc/rc.local
```
Use Ctrl-X to exit if I remember right.

Where I am, these forums are pretty-much unusable with that block in place - pages don't finish loading.

---

### Post by shane_faulkinbury2 on 2015-11-29
Thanks!  Done, saved and will reboot later to see if that did the trick!  The thing with Akamai is they have thousands of IPs  so I will have to keep an eye out to ban each cluster I see!

---

