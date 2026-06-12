---
title: "How to become root user in ubuntu 17.10"
date: 2018-01-20
forum: General Help
---

### Post by sleepingpills on 2018-01-20
For  the first time i am installed ubuntu 17.10 in my pc but I don't know  how to become root user in terminal. Please help me to resolve this  problem.

---

### Post by vasa1 on 2018-01-20
Why do you need to become root user? Just use *sudo*.

---

### Post by yancek on 2018-01-20
To expand on the comment above, the initial user created upon installing Ubuntu has root privileges using sudo.   For a complete and detailed understanding of 'sudo' and it's advantages/disadvantages, see the link below to the official Ubuntu Documentation.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by hojzak on 2018-03-09
I have the same problem but I can not use sudo. It says my user is not in sudoers file.

---

### Post by wildmanne39 on 2018-03-09
Hello hojzak, please start you own thread you will be more likely to get your issue resolved.

Thanks

---

### Post by HermanAB on 2018-03-09
Reboot into single user mode and edit the /etc/sudoers file.  A little googling will get you going.

---

