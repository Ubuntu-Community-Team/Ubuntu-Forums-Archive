---
title: "Problem With Group Permissions"
date: 2007-05-25
forum: General Help
---

### Post by DoctorDemento on 2007-05-25
Still new to Linux and I am having a problem with group file permissions. I am using gEDA electronic schematic editor within Feisty and wish to edit the schematic symbols. The symbol directories and files were u=root rwx g=root r-x o= -r-. I changed the group to 'users' of which I am a member. I still cannot save edited symbols to the directory unless I change the user of the directory to my user name. The current settings are u=root rwx g=users rwx o=-r-.

---

### Post by m.musashi on 2007-05-26
It's probably not a good idea to change owership of root files and directories. Things probably won't work well. I think it would be better to make a new group and make both you and root members and then set that group as the owner. You can open the user and groups tool under system -> admin. From there you can make a new group and set the members.

This is just an idea so I can't guarantee it will work. Keep track of what you do and undo it if need be. Maybe someone else has a better option.

---

