---
title: "how to add user into group??????"
date: 2007-07-01
forum: General Help
---

### Post by virushioyo on 2007-07-01
useradd tp -d /home

but the tp din appear in /home dir.

how can i add a new user and put them into /home dir? please guide.

appreciate ya'll help. thanks.

---

### Post by raja on 2007-07-01
```
adduser tp tpgroup
```

---

### Post by virushioyo on 2007-07-01
> **virushioyo said:**
> i created a user named tp and a group name tpgroup. so now, how can i put tp into tpgroup. please help. thanks

appreciate ya'll help.

sorry guys. it my mistake

i use adduser [groupname] username instead of adduser username [groupname].

---

