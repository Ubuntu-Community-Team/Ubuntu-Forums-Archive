---
title: "[SOLVED] how to add user to a group"
date: 2008-05-31
forum: General Help
---

### Post by cybergalvez on 2008-05-31
How do I add a user to a group? I thought you used usermod so when I did sudo usermod -G newgroup user followed by a id user I saw that I really messed everything up and now all the old groups that the user belonged to he no longer belonged to.  So how should I have done it?
Jose

---

### Post by koshari on 2008-05-31
you can do it through the gui using administration>user/groups,

or manually by add ing :user to the group line in the group/users file.

---

### Post by cybergalvez on 2008-05-31
The group I wanted to add the user to was not listed in the gui (don't know why) 
so is manually editing the group file the best way? because I thought there was a shell command to do it
Jose

---

### Post by Iowan on 2008-05-31
**usermod** would seem to be the command to use, but the **man** page mentions:```
-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
... If the user is currently a member of a group which is not listed, 
the user will be removed from the group. This behaviour can be changed via -a option,
 which appends user to the current supplementary group list.
``` I suspect you listed only the group(s) to be added.

---

### Post by scottro on 2008-05-31
To add user bob to the wheel group
(Personally, I find the man page somewhat confusing in its explanation, and examples would have been helpful, but...)

usermod -G wheel -a bob

There is also gpasswd

gpasswd -a bob wheel

That will also add bob to wheel without removing him from other groups.

---

### Post by cybergalvez on 2008-06-01
thanks for the reply's I did get the usermod command wrong or rather I missed adding the "-a".  Thanks
Jose

---

### Post by scottro on 2008-06-01
Glad it helped.  The man page is very poor.  The order of the options is important, and the man page gives little or no indication of that.

---

