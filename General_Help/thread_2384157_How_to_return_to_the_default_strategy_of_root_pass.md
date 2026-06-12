---
title: "How to return to the default strategy of root password in Ubuntu16.04?"
date: 2018-02-03
forum: General Help
---

### Post by yys2 on 2018-02-03
hi all,
I am using ubuntu16.04 which has a strategy for the root password. This strategy means that Ubuntu has no default password for root and it has a random password for root every time I login. This strategy is nice. 
But I set my root password by mistake today. How can I return to the default strategy for the root password?

---

### Post by deadflowr on 2018-02-03
To disable and lock any password run
```
sudo passwd -dl usernamehere
```
so for root run as
```
sudo passwd -dl root
```
more here: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

