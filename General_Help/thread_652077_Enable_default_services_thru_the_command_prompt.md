---
title: "Enable default services thru the command prompt"
date: 2007-12-28
forum: General Help
---

### Post by Mr.Johnny on 2007-12-28
I disabled some services in ubuntu 7.04, and now I always get a "fail to initialize hal" error on startup.

When I try to go to the services menu again (even as root), I get a 
"You are not allowed to access the system configuration" error.

I don't want to reinstall ubuntu... :-( How can I solve this?

thanks.

---

### Post by taurus on 2007-12-28
Do you belong to groups adm & admin?  What's the output of this command from a terminal?

```
id
```

---

### Post by Mr.Johnny on 2007-12-28
it says:

uid=0(root) gid=0(root) groups=0(root)

---

### Post by taurus on 2007-12-28
You logged in as root!  Try log in as a regular user and run that command again.

---

### Post by Mr.Johnny on 2007-12-28
Oh, sorry about that...

Checked... I am not in the adm/admin groups. Sorry, I am noob, how do add my user to those groups?

---

### Post by taurus on 2007-12-28
You can edit /etc/group and add your *username* to groups adm & admin or you can log back in as root now and run it from a terminal

```
adduser *username* adm,admin
```

---

### Post by Mr.Johnny on 2007-12-28
ops... 

now I realized the id command gives me the groups of the current user... I interpreted something else.

I was mistaken, adduser reports I am already in those groups, and even as a root, it says "You are not allowed"

It must have something to do with the services I disabled. :(

---

### Post by mellowd on 2007-12-28
try this and see what happens:

```
sudo adduser username adm,admin
```

---

### Post by Mr.Johnny on 2007-12-28
I did it for my user, same thing (already added). Did it for root, and it said it was added (wasn't it supposed to be part of those groups or did I do something stupid?).

But it still says I am not allowed to access the system configuration... :( time to format?

---

### Post by artinla on 2007-12-28
Sorry, I misread your post.  No help here.

Good Luck,

Art

---

### Post by Mr.Johnny on 2007-12-28
Format it is... :D

Thanks to all anyway, I learned some stuff.

---

