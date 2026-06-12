---
title: "What users are in a linux group"
date: 2007-01-23
forum: General Help
---

### Post by frankabel on 2007-01-23
How can I see all the users that belong to a group?

Salute
Frank Abel

---

### Post by mizar001 on 2007-01-23
I think that /etc/group is the file you mean search in.

For example for the GGG group :

$cat /etc/group |grep GGG:

And you should see a listing of users that belong to GGG group. If there's no one probably there's a user in it having the same name.

---

### Post by frankabel on 2007-01-23
man group say:
> 
BUGS
       As  the  4.2BSD  initgroups(3)  man  page  says:  No-one  seems to keep
       /etc/group up-to-date.


and that's true.. in my system exist the group **users** with some users belonging ti it and /etc/group don't show that

Thanks anyway

Salute
Frank Abel

---

### Post by mizar001 on 2007-01-23
But this 'users' group is defined at least among users in '/etc/passwd' file ? I thougth /etc/group was the file to reference to for groups.

When i do 'sudo groupadd groupname' my groupname appears correctly in the /etc/group file.

Also calling a group 'users' is something misleading.

---

### Post by frankabel on 2007-01-23
The group **users** is a system default and is on /etc/group file (check in your system). The problem is that in that file don't appear the users belong to it. 

Salute
Frank Abel

---

### Post by mizar001 on 2007-01-24
Is this done ever for others groups and users belonging to it ?

I now tested adding a new user to the 'users' group and it appears correctly in /etc/group

Ho you make and add users to groups ?

---

### Post by frankabel on 2007-01-24
well... really I don't add any user to any group... just create a user and then is created an group for it... and that group don't have the list(in the /etc/group file) of users that belong to it.

For example:
useradd test
grep test /etc/group
test:x:1010:

Salute
Frank Abel

PD: I speak about the group **users** due to that server was a debian server before but now is a ubuntu (the chage was made editing the source.list file) so when a new user was created the group that it belong was **users** instead of a group of the same name that the user like now in ubuntu.

---

### Post by mizar001 on 2007-01-25
Actually i've a breezy server distro installed, and if i do what you done i obtain no new group, except that this user is added to 'users' group.

On another distro (edgy desktop) i do the same thing and the result is the same as you.

Probably the behavior in edgy is this :
When you create a user, a group with the same name is created. This group has a list of members to it, but if there's no list then probably a user with the same name is belonging to it.
In other words groups does not exist without almost 1 user, unless you explicitly create a group with groupadd.

In the latter case from /etc/group it's impossible to state if a group has a user with the same name.

---

### Post by frankabel on 2007-01-25
So the bug described at **man group** is true... I then repeat my question again... exist any way of determine all the users that belong to a group in ubuntu?

Salute
Frank Abel

PD: I know that I can build an script based  **groups** command (asking in what group each system user are) but I want another more simple way.

---

