---
title: "Samba, restrict users"
date: 2015-09-24
forum: General Help
---

### Post by Drenriza on 2015-09-24
Hi all

I have a samba share where login is based on groups.

My question is if its possible to do something like
```
[share1]
writable = yes
browseable = yes
path = /path/1
valid users = @group1
```


And than add users to @group1 with all the group permissions, but NOT giving them access to share1
Something like
```
[share1]
writable = yes
browseable = yes
path = /path/1
valid users = @group1
SomeDeny/blockOption = newUser1 newUser2
```

The reason i want to do this is that newUser1 and newUser2 need access to a folder in the share1 drive (and nothing else), which i think i will symbolic-linked to another drive
newUser1 and newUser2 can access. And than deny them access to share1 (everything else).

Thanks on advance
Kind regards

---

### Post by Drenriza on 2015-09-28
```
invalid users = user1 user2
```

---

