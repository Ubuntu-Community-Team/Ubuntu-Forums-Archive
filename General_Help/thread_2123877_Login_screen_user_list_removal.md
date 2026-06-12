---
title: "Login screen user list removal"
date: 2013-03-09
forum: General Help
---

### Post by techyknowsbest on 2013-03-09
I want to remove the user list from the login screen on Ubuntu 12.10. I've tried using gconf-editor and using a terminal line to no avail. Can someone offer advice to me please?

Jake

---

### Post by Cheesemill on 2013-03-09
You need to edit the lightdm configuration file. To do this hit ALT+F2 and run the following command...
```
 gksudo gedit /etc/lightdm/lightdm.conf
```
Add the following line to the bottom of the file...
```
greeter-hide-users=true
```
Save the file and reboot and the user list will be hidden.

---

