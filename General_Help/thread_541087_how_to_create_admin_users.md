---
title: "how to create admin users"
date: 2007-09-02
forum: General Help
---

### Post by suj2007 on 2007-09-02
Will anybody plz tell me how to create admin users through terminal window?

---

### Post by taurus on 2007-09-02
The first user on your system has a root privilege and if you want to add other users to that list, then you need to add them, their usernames, to both groups adm and admin in /etc/group.

```
sudo nano -Bw /etc/group
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by banewman on 2007-09-02
The command is - gksu users-admin - then it will ask for the admin password - then bring up the users & groups GUI.

---

### Post by suj2007 on 2007-09-02
I have deleted the user which was created during installation of Ubuntu.
Now there is a user which was also created during installation for accessing windows my documents etc. 
By login through that user i can get the root previligae in terminal window. but do not get admin previligae in GUI. 
Therefore I wish to create a user exactly like a user which was created during installation. Please guide me step by step

---

### Post by aysiu on 2007-09-02
**Step 1**
Reboot

**Step 2**
Select *Recovery Mode*

**Step 3**
At the command prompt, type ```
adduser *username* admin
``` where *username* is the name of the user you want to be an administrator.

**Step 4**
Reboot ```
reboot
``` and boot into the normal mode.

---

### Post by suj2007 on 2007-09-02
> **aysiu said:**
> **Step 1**
Reboot

**Step 2**
Select *Recovery Mode*

**Step 3**
At the command prompt, type ```
adduser *username* admin
``` where *username* is the name of the user you want to be an administrator.

**Step 4**
Reboot ```
reboot
``` and boot into the normal mode.

As per the above guidence I  have created admin user. Now I can access all the application in system>administrator.

Also please tell me user ID = 1001 or 1000 which is most powerfull 
System>Administrator>user & group>properties>advance> user id = 1000.

---

