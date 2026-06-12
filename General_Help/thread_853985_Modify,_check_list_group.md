---
title: "Modify, check list group"
date: 2008-07-09
forum: General Help
---

### Post by niqmk on 2008-07-09
Hello, Good day
I wanna ask how to modify the user group that i've created.
And how can i make a list of group that i've created before because i've forgot a name of group. when i tried to groupadd virtual -g 5000 (groupadd: GID 5000 is not unique). Thank you.

---

### Post by iaculallad on 2008-07-09
Navigate to System->Administration->Users and Groups, click on "Manage Groups" -> select the group you want to manage on the list and click on "Properties".

---

### Post by niqmk on 2008-07-09
how about command in terminal. cos i'm using server

---

### Post by iaculallad on 2008-07-09
On terminal:

```
groupmod
```

For the options, try reading it's man page.

```
man groupmod
```

---

### Post by niqmk on 2008-07-09
Ok, Solved.
Thank you. I didn't read a FM.

to change
groupmod -g 5000 vmail -n virtual
to check a list
vi /etc/group

---

