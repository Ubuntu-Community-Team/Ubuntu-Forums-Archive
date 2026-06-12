---
title: "Trying to Write a Basic Command Script"
date: 2007-12-14
forum: General Help
---

### Post by bsalt on 2007-12-14
Hey guys, I have a PCI wireless card I installed in my desktop, and many times it will lose the connection, but NetworkManager will not automatically try to reconnect. I have found doing the following commands will work:

killall NetworkManager
killall NetworkManagerDispatcher
killall nm-applet
rmmod rt61pci
NetworkManager
NetworkManagerDispatcher
nm-applet
modprobe rt61pci


I want to write a script that will do this all at once. Does anybody know how to help me with this?



Does anybody know of a better way to repair a wireless network?

---

### Post by bsalt on 2007-12-14
Ok, I realized that adding a ; in between two commands can work. Here's my script (so far). Let me know if anybody finds a problem.


```
#!/bin/bash


read -p "Your network will be repaired. Press any key to continue..." 
gksu "killall NetworkManager;killall NetworkManagerDispatcher;killall nm-applet;rmmod rt61pci"

read -p "One more step..."

gksu "NetworkManager;NetworkManagerDispatcher;nm-applet;modprobe rt61pci"

clear
read -p "$USER, Network is Repaired"
```

---

