---
title: "Set permissions on shared folder"
date: 2021-05-04
forum: General Help
---

### Post by josedarm on 2021-05-04
Good afternoon,

i am trying to set a shared folder to be accessible via network for 2 users: teachers and students.

Teachers to have full access and students read only.

I set teachers as owner of the shared folder and changed the group they are in "teaching".

When I access this shared folder from the teachers side it is only letting me to read. It does not allow copying files or delete. Then when I "Allow others to create and delete files in this folder" from the gui, it give full permission to both students and teachers and can copy and delete.

I am new to the ubuntu enviroment so not sure what I am doing wrong.

Can someone help?

Regards

Joseph

---

### Post by Impavidus on 2021-05-04
Permissions for the group must be set to read and write (and execute for directories or executable files), permissions for others must be set to read (and execute for directories or executable files), but no write.

---

### Post by Morbius1 on 2021-05-04
> Then when I "Allow others to create and delete files in this folder" from the gui
You created a samba usershare from Nautilus. You cannot do what you want using this method.
> I set teachers as owner of the shared folder and changed the group they are in "teaching".

I would suggest undoing the nautilus share and create 2 shares of the same folder in /etc/samba/smb.conf itself. Something like this:

```
[Shared-Teachers]
path=/path/to/shared/folder
guest ok = no
read only = No
valid users = @teaching
force user = teachers
```

```
[Shared-Students]
path=/path/to/shared/folder
guest ok = no
read only = Yes
```

Then restart smbd:
```
sudo service smbd restart
```

The [highlight]valid users = @teaching[/highlight] will prevent everyone other than members of that group from accessing the share. So one share is writeable to teachers the other read only to everyone else.

---

