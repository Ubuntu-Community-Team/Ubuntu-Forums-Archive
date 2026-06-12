---
title: "sudo in the terminal"
date: 2008-06-19
forum: General Help
---

### Post by ZeldaFan on 2008-06-19
When I use a command involving "sudo" in a terminal, I must type in my password (obviously). However, while I am in the same terminal session, if I ever use sudo again, I do not have to retype my password. How can I change my settings to make me have to type the password everytime I use sudo instead of just once every terminal session.

---

### Post by bodhi.zazen on 2008-06-19
You have to configure sudo

Open a terminal and enter :

```
sudo visudo
```Under the options section add **passwd_timeout**=0 at the end of the line.

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

---

