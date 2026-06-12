---
title: "Looking for a Good Dialup ISP for use with Ubuntu/WinXP"
date: 2005-08-20
forum: General Help
---

### Post by darkstar5680 on 2005-08-20
Right now, I have PeoplePC online Dialup servive, which is cheap, but I can't seem to figure out how to connect th them in Ubuntu.  In windows, they use a special dialer app.  I'm looking for a good dialup ISP which can be used in Linux and windows, and is not too expensive.

Unless, someone knows how to connect with peoplePC in Linux...

---

### Post by adwait on 2005-08-20
I don't really know about your specific ISP, but have you tried 
```
sudo pppconf 
```
?

---

### Post by minio on 2005-08-21
At first you have to find:
phone number used to connect to your ISP
your username and password you use to connect to your ISP
IP adressess of DNS servers your provider use


 
Try to install gnome-ppp and use it instead of default gnome dial up utility.

---

