---
title: "File Permission problem on Edgy"
date: 2007-06-21
forum: General Help
---

### Post by achimwene on 2007-06-21
Hie 

I have installed Kubuntu 6.10 . I then installed samba mainly for file and directory sharing . I have tested , users can logon fine from windows XP machines . However , only the user defined as the owner of a directory can access it , users in the group cannot . Even after defining the group as owning the file also , access is still not permited . However I then noticed that it has more to do with the OS than samba as I logged on with CLI as a group user , and cant cd to that directory .

please help

achimwene

---

### Post by atria on 2007-06-21
You'll need to change the directory permissions.

I'm afraid that is not going to be as simple as you might think but heres the simple method:

```
chmod 755 <path_to_foldername>
```

755 means, give read/write/execute access to owner, read/execute permissions to group members and read/execute permissions to everyone.

If you need more security then perhaps change it to 750, but you'll have to ensure that the folder belongs to the group.

```
chgrp <groupname> <path_to_foldername>
```

If the above commands do not work because of lack of permissions, just add sudo infront.

---

### Post by Qu4k3R on 2007-06-21
you could use also 
> 
sudo chown <your username here> <path_to_foldername>


---

