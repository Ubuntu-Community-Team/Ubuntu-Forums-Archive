---
title: "Unable to get group access to a specific folder"
date: 2013-08-25
forum: General Help
---

### Post by ndnd on 2013-08-25
Hi I am trying to  get access to "brian_g" folder it's file permissions are 

> drwxrwx---  2 blakin brian  4096 Aug 25 15:48 brian_g


My username has been added to group "brian" 

when I do my id it shows me added to the group brian 

However whenever I try to 
> cd brian_g/
-bash: cd: brian_g/: Permission denied

I have done the following command to give ownership access

> sudo chmod -R ug+rwx /shared/brian_g/

Thanks in advance.

---

### Post by steeldriver on 2013-08-25
Did you log out and back in again after adding your username to the 'brian' group? although 'id' will show the change immediately, it won't really take effect until next login (although technically I think it's sufficient to spawn a new login shell with [FONT=courier new]su -- *username*[/FONT]  ... if you want to get tricky)

---

### Post by ndnd on 2013-08-25
Thanks again steeldriver.
It worked.

---

