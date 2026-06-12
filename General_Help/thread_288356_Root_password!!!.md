---
title: "Root password!!!"
date: 2006-10-29
forum: General Help
---

### Post by badguyanil on 2006-10-29
While installing ubuntu it asks for a hostname (name by which my comp will be recognised in a n/w), a user name and a password. Well i can login using this username and pwd alright. But how do i login as root (new to linux, and if i am not worng root has all the previliges on the system)!

---

### Post by llamakc on 2006-10-29
Ubuntu doesn't enable root with a password by default. You should use the "sudo" command to execute administrative tasks on the commandline. When you use sudo, it will ask for YOUR password.

Otherwise, enable root's password.

```

sudo passwd root

```

It will ask for YOUR password first.

---

### Post by PriceChild on 2006-10-29
This was explained first time you openned a terminal.

Check out [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) for more information.

---

### Post by aysiu on 2006-10-29
If you're more of a point-and-click person, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by badguyanil on 2006-10-30
Great help! thanks!will start with with the "point-and-click" method....but i seem to be liking the terminal..shld have tried linux much earlier!!!!   Thanks a lot for ur replies.

---

