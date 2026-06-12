---
title: "Cant delete my group"
date: 2013-09-27
forum: General Help
---

### Post by mast3rmind2 on 2013-09-27
Hi,

My problem is i created a user so the group was automaticly created but now i want to deleat the group of that user but its impossible, i get a message of 'padmin' still has 'MaSter' as their primary group. i tried to create diffrent users so i can put them in the primary group but its seems not working
Im a beginner and i spend few hours to fix this problem i cant do anything please help me out.

---

### Post by Gyokuro on 2013-09-27
In case MaSter is the group you want to delete:

sudo groupdel MaSter

however I would delete at first the user:

to find out to which group the user belongs:

sudo id -nG usernamewhichshouldgetdeleted

then delete the user:

sudo usermod -G MaSter usernamewhichshouldgetdeleted

---

### Post by steeldriver on 2013-09-27
From [FONT=courier new]man groupdel[/FONT]
```

CAVEATS
**       You may not remove the primary group of any existing user. You must remove the user before you remove the group.**

       You should manually check all file systems to ensure that no files remain owned by this group.

```

If you want to remove a group that is currently a user's primary group,  but NOT remove the user, then you will first need to assign a new  primary group for the user i.e.

```
sudo usermod -g *newprimarygroup* *user*
```

From [FONT=courier new]man usermod[/FONT]
```

       -g, --gid GROUP
           The group name or number of the user's new initial login group. The group must exist.

           Any file from the user's home directory owned by the previous primary group of the user will be owned by this new group.

           The group ownership of files outside of the user's home directory must be fixed manually.

```

---

### Post by mast3rmind2 on 2013-09-27
Thanks problem solved. :p

---

