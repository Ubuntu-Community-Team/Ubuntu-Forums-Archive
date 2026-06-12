---
title: "you do not exist in the passwd database"
date: 2023-03-21
forum: General Help
---

### Post by renatoseres on 2023-03-21
I use Linux a lot of years, but I've made a big mistake in my Ubuntu 22.04.1 LTS box

I am the only Linux Admin in my Ubuntu box

I allways logged user with my user - renatolinux 
and used sudo in the privileged neeeded commands 

I tried to use some commands without success - sudo cd in some folders I could not use , so I tried to change my user to a superuser

In /etc/passwd my user was:

renatolinux:x:1001:1001:renatolinux:/home/renatolinux:/bin/bash

I changed with vim to:  
renatolinux:x:0:0:renatolinux:/home/renatolinux:/bin/bash

(in past times, I dit this in other Linux boxs, without problems)

Using id, it seems all is normal:
# id renatolinux
uid=0(root) gid=0(root) groups=0(root)

# more /etc/passwd |grep renatolinux
renatolinux:x:0:0:renatolinux:/home/renatolinux:/bin/bash

BUT:
1- error in several commands now:

#sudo more /etc/passwd
sudo: you do not exist in the passwd database


# sudo mcedit /etc/passwd
sudo: you do not exist in the passwd database

# sudo add user renatolinuxTWO
sudo: you do not exist in the passwd database

2- I cannot log anymore in terminal via ssh from another putty session
Access Denied


Thank you !!

---

### Post by Holger_Gehrke on 2023-03-21
What an interesting new way to break an Ubuntu system ! root isn't allowed to login on Ubuntu, by changing you id to 0 you become root, so you're not allowed to login. Time to boot up a live system, mount your root file system and undo the changes you made.
BTW, 'sudo cd' can't work because cd is an internal command of the shell so there's no 'cd' executable for sudo to run.

Holger

PS: for an interactive root session you can use 'sudo -i'
PPS: please put terminal input / output in [noparse]```
...
```[/noparse] BBcode tags for better readability
PPPS:and while you're at it, you can disable parsing for emoticons with a checkbox at the botton of the advanced mode of the editor ...

---

### Post by renatoseres on 2023-03-23
Thank you !

---

### Post by SeijiSensei on 2023-03-23
Usually the default user with sudo privileges on Ubuntu has ID 1000, not 1001. So you might have one user with sudo privileges, but not the one with ID 1001.

Also you do not need root privileges to view /etc/passwd (or /etc/group). Just "more /etc/passwd" is enough. You do need root privileges to edit it.

---

### Post by renatoseres on 2023-03-23
the Linux is in a POXMOX Virtual Machine

Is there a way that a live CD can accces the filesystem of this VM ?

---

### Post by SeijiSensei on 2023-03-24
If it's just running in a VM, I'd blow that away and reinstall.

---

### Post by renatoseres on 2023-04-24
I found out a better solution:

Enter in Linux recovery mode and fix 
How to enter in the recovery mode (same procedure when we lost the Linux admin password)

[https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

---

