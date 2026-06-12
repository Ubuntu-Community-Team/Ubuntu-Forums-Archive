---
title: "I dont think I made myself an admin"
date: 2008-03-22
forum: General Help
---

### Post by fruni on 2008-03-22
When I try to do a sudo command or do something that I need to be an admin to do it says:
fruni is not in the sudoers files. This incident will be reported.


so... how do I add myself into the sudoers file? BTW I am new to ubuntu :D

---

### Post by fruni on 2008-03-22
Now when I try to use sudo I get this error: 
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory. :D thanks for reading this.

---

### Post by ruibernardo on 2008-03-22
Hi Fruni,

you have to add your username to the "admin" group. To do it, reboot in the recovery mode and on the console type:

```
adduser *your_username* admin
```Now that user belongs to the admin group and can do everything with sudo. Reboot in normal mode and try it. Every user in the admin group can run commands with sudo without limitations.

More info about sudo and root: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by fruni on 2008-03-22
Thanks alot :) I really love this community, I got help pretty fast :)

---

