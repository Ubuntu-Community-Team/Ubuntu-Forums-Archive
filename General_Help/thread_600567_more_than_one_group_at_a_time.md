---
title: "more than one group at a time"
date: 2007-11-02
forum: General Help
---

### Post by fazavon on 2007-11-02
All right, I have been trying for two days to get this working. 

In Fedora/Redhat to add a user to more than one group at a time all you have to do is

adduser username -G DSales,DMarketing,DAdmins

Now in Ubuntu and Debian when I try this I get one of two things.

1st 

Man page on how to use adduser (that has been no help for this issue)

2nd

adduser: Only root may add a user or group to the system.

I know what you first question will be here is what I have tried

adduser username -G [group1,group2]
adduser username -G group1 group2
adduser username -G group1,group2
adduser username -G {group1,group2}
adduser -G username  [group1,group2]
adduser -G username  group1 group2
adduser -G username  group1,group2
adduser -G username  {group1,group2}
adduser username  [group1,group2]
adduser username  {group1,group2}
adduser username  group1 group2
adduser username  group1,group2

I have also tried -g and with out commas in the brackets and braces.

Does anyone know how to add a user to more than one group at a time. 

Thank you in advance

//j

---

### Post by ecschiel on 2007-11-03
It seems that u are running the commands from a non root account. If your acount have admin rights (if it's the first one created it has) just prepend sudo at the command
```
 sudo adduser username -G DSales,DMarketing,DAdmins
```
this will ask you for your password and execute the command.

---

### Post by fazavon on 2007-11-03
No to save time i had run sudo -i first. so my prompt looked like root@machinenema:#

---

### Post by fazavon on 2007-11-08
bump

---

