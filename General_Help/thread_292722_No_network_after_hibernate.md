---
title: "No network after hibernate"
date: 2006-11-04
forum: General Help
---

### Post by PuleX on 2006-11-04
I was playing around with the settings and preferences, just to get a feel for the improvements in Edgy, and one of the things I did was configure the Power Management options (System > Preferences > Power management). 

I selected that my pc should go to sleep after 30 minutes. And that really worked! And when I started the pc again it brought my right back to my desktop with all apps running. (Nice!) 

However, I couldn't reach the internet anymore after that. A network restart fixed this: 
```
sudo /etc/init.d/networking restart
```

Has anyone experienced this and found a fix for the networking problem?

---

### Post by PuleX on 2006-11-04
All right, I forgot to do a launchpad search before posting.  ;-) 
This seems to be an acpi-support scripts bug: 

[https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/69892](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/69892)

---

