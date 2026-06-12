---
title: "Problem on running groupadd"
date: 2007-12-12
forum: General Help
---

### Post by satimis on 2007-12-12
Hi folks,


Ubuntu 7.04 server amd64


I need to create a new group, vmgroup, adding userA, userB as member to the gourp;


On running;

$ sudo groupadd -g 123 -x members=userA,userB vmgroup

I can't find the extended option -x


Please advise how to overcome this problem adding members to the new group.   TIA


B.R.
satimis

---

### Post by geirha on 2007-12-12
I don't think you can do that in one go like that (unless you edit /etc/group manually)

Try with addgroup and adduser like this:
```
sudo addgroup vmgroup
sudo adduser userA vmgroup
sudo adduser userB vmgroup
```

---

