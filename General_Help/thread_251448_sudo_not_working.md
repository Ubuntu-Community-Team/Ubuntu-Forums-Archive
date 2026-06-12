---
title: "sudo not working"
date: 2006-09-05
forum: General Help
---

### Post by mwolfe on 2006-09-05
alright i recently did an update, and one other change to my system, and now sudo is not working.. i can't get to synaptic or anything else..
I get an error that says "failed to run /usr/sbin/synaptic
the underlying authorization mechinism (sudo) does not allow you to run this program. Contact the administrator."


Now the only other thing i've done was add myself to the games group by issuing the command

sudo usermod -Ggames mwolfe

could this have messed up my system?

thanks

---

### Post by taurus on 2006-09-05
You need to belong to both adm & admin.  See if you do with this command, from a prompt!

```
id
```
If not, boot it into recovery mode (from GRUB) and add yourself to those two groups in /etc/group.

```
nano /etc/group
```

---

