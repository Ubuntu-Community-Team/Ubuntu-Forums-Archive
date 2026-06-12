---
title: "Help - {help} add remove programs problem in ubuntu"
date: 2008-01-12
forum: General Help
---

### Post by dr_gauravsuneja on 2008-01-12
recently while installing screenlets in ubuntu as given in ubuntu customization guide i have changed the repositories links and added repository list of screenlet server in ubuntu add remove program servers in third party software tab .now i am unable to open synaptic package and add remove program it says to change the things in sources.list .i have found sources the list in etc/apt/source.list but not able to save it .am i doing the right thing? how to solve it?how to login as root as i don't have root user privilege what is root login is and user name?
thanks in advance
[[IMG]http://img186.imageshack.us/img186/8387/screenshotxk6.th.png[/IMG]](http://img186.imageshack.us/my.php?image=screenshotxk6.png)

---

### Post by Thingymebob on 2008-01-12
Hit Alt+F2 type: gksudo gedit /etc/apt/sources.list

The password is the one you used when you installed Ubuntu. You will be able to save your changes

---

