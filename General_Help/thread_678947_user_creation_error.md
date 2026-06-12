---
title: "user creation error"
date: 2008-01-26
forum: General Help
---

### Post by freesun on 2008-01-26
This is plain stupid. When I try to create a user, ubuntu does nothing (does not create him). I thought Linux is meant to be multi-user system... I have latest updates. Before updates the user was created until he tried to log-in. Please help, this is very stupid situation for a linux-based OS...

---

### Post by taurus on 2008-01-26
Before you start calling everything else stupid, what exactly did you do to create another user?  Did you do it from GUI or from terminal?

---

### Post by freesun on 2008-01-26
Well 1st: I'm not calling ubuntu stupid, I'm calling situation stupid and it is for sure...

2nd I did use GUI, I entered nickname, password and confirmed password... Worked on Dapper, worked on Edgy, worked on Feisty...

---

### Post by taurus on 2008-01-26
Which GUI?

---

### Post by freesun on 2008-01-26
Well i use SK localization...
But I guess in english it would be System->Administration->Users and Groups...

---

### Post by taurus on 2008-01-26
What are the outputs of these commands from a terminal?

```
ls -la /home
cat /etc/passwd
```

---

### Post by freesun on 2008-01-26
the home directory of user does exist, however he is not in passwd file (which I know what it is for ;)

so? conclusions?

Yes I deleted user and tried to re-create it...

---

