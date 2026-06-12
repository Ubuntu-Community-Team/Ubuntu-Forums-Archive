---
title: "Mysql doesnt start on system boot"
date: 2007-09-09
forum: General Help
---

### Post by fernando_lopes_jr on 2007-09-09
I installed mysql sow I can use it with amarok for music data base but unless I use the comand:

sudo /etc/init.d/mysql restart

to start the data base mysql want boot up when I start ubuntu can someone give me a hand with this plz. Thx

---

### Post by fernando_lopes_jr on 2007-09-10
Can anyone give me a hand?

---

### Post by visik7 on 2007-09-11
same problem here
I'm inspecting about this

---

### Post by visik7 on 2007-09-11
got the problem
vim /etc/mysql/my.cnf
bind-address is binded to an ip of the vmware virtual machine
dunno why :)
check your too
I've put 127.0.0.1

---

