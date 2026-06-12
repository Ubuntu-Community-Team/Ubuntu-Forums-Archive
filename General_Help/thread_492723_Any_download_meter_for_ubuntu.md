---
title: "Any download meter for ubuntu ?"
date: 2007-07-05
forum: General Help
---

### Post by saurabh kakkar on 2007-07-05
hi
   i am new to linux and have limited internet connection. I wana know is there any download meter which can help me analyze my upload and download Mbs  ? if yes plz do provide the step on how to install .

---

### Post by dfreer on 2007-07-05
GUI based:
System > Administration > System Monitor. Click on the "Resources" Tab, it's at the bottom under "Network History"
It's installed by default.

CLI based:
```
sudo apt-get install ethstatus
```
```
ethstatus -i **eth0**
```
Replace eth0 with your internet interface (you can find this out with the command: ifconfig)

---

