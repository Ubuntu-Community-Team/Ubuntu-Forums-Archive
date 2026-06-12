---
title: "network settings have mind of their own"
date: 2008-03-19
forum: General Help
---

### Post by nephish on 2008-03-19
hey there all,
i have a static ip set up in /etc/network/interfaces

and when i do /etc/init.d/networking restart it comes up correct, but then later, it's ip 
address suddenly changes, like it got one by dhcp. 

if i restart the network, everything is ok again.

i did removed the gnome-system-tools that include the network config dialog, but it is still happening.
sometimes takes a few hours, but eventually winds up changing it's address.

also, cant seem to keep eth1 from loading.

i can do sudo ifconfig eth1 down, and it goes down but then a little while later it shows back  up in ifconfig ( though usually not with an ip address, nothing is plugged into it)

any tips would be appreciated a lot.
thanks

---

