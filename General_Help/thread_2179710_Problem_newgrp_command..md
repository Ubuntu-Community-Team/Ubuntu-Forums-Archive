---
title: "Problem newgrp command."
date: 2013-10-09
forum: General Help
---

### Post by RH3dDbz on 2013-10-09
Hello, I have problem using the newgrp command, when I write:

newgrp client

then the command ask me for password, after I write down the password and press the button enter, the command tell me that the password is not valid, the password I input is the same password I use to login, do I have to setup something special to use this command?.

 In old version of Ubuntu had program in the graphical enviroment that allow me to create user and group, the program called "User and group", I don't remember exactly the name of the program, now in the Ubuntu 12.04 LTS I don't have this program, can I install this program again?, and how can I see the group that already exist?, thanks in advance.

---

### Post by bab1 on 2013-10-09
> **RH3dDbz said:**
> Hello, I have problem using the newgrp command, when I write:

newgrp client

then the command ask me for password, after I write down the password and press the button enter, the command tell me that the password is not valid, the password I input is the same password I use to login, do I have to setup something special to use this command?.

 In old version of Ubuntu had program in the graphical enviroment that allow me to create user and group, the program called "User and group", I don't remember exactly the name of the program, now in the Ubuntu 12.04 LTS I don't have this program, can I install this program again?, and how can I see the group that already exist?, thanks in advance.

Newgroup is not for adding groups or adding users to existing groups.  See the man page ```
man newgroups
```

I think what you want is addgroup.  See the man pages for addgroup ```
man addgroup
```

---

### Post by RH3dDbz on 2013-10-09
Hello bab1, thanks for replying, I want to change from group to one of my user.

---

### Post by RH3dDbz on 2013-10-10
Thank you, I found solution how to change the group to which a user belongs, and how to see the list of group already exist, I install the program called "User and Group".

---

