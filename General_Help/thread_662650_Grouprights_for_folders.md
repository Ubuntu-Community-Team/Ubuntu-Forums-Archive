---
title: "Grouprights for folders ?"
date: 2008-01-09
forum: General Help
---

### Post by Reeva on 2008-01-09
Hello,

I have a samba server with a shared folder accessable for everyone, let's call this folder 'sharefolder'.

In the samba config file, I use this:

```

[allusers]
  comment = All Users
  path = /home/shares/sharefolder
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes

```

So alle the users from the group ' users ' have acces to this share.

On a windows machine, I go to the share, login with the samba username & password for the user "marc" , and I see the sharefolder.

Now I can make a new folder, put files in it etc. (as user marc)

When I go to another windows machine and login as ' alexander ' (for ex), I see the share again, with the directory that "marc" made .. But now I want to delete this folder from my alexander account..

But this doesn't work, as I have no permission to do that?

So what I want is a global folder on the samba server where every user from the " usersgroup " can edit / delete / remove .. files and subfolder..

How can I do that? :confused:

thank you

---

### Post by Caligatio on 2008-01-09
Can you check the owner/group and the current permissions on the folder that Marc created?

---

### Post by geirha on 2008-01-09
Try setting directory mask to 2771 instead of 0771. The 2 sets the setgid bit, which will make it inherit group-ownership

---

### Post by Reeva on 2008-01-09
I changed the samba file to the following conf:

```

[gedeelde_server]
path = /home/shares/sharefolder
comment = shared folder for all users
available = yes
browsable = yes
public = yes
writable = yes

```

and this works the same ..

also setting directory mask to 2771 instead of 0771 didn't work

@ Caligatio: the permissions are 

-rwxr--r-- 1 marc users 569 2007-12-22 11:21 file.txt


so marc has all the permissions, an the group just ' read' ..

how can I solve that everyone can use and delete the folder from marc?

thank you

---

### Post by Caligatio on 2008-01-09
The underlying issue is the group isn't getting write permissions on the file.  Readd the create mask = 0660, directory mask = 0770, force group = users, and restart the server.  Then just try to create the file again and see what the permissions are.

For instance, my similiar share is:

[Private]
   comment = Family Only Share
   path = /path/to/files
   valid users = @family
   writeable = yes
   create mask = 0660
   directory mask = 2770
   force group = family

---

### Post by geirha on 2008-01-09
I did a quick read of the smb.conf man-page. It appears you need to use **force directory/create mask** instead of just **directory/create mask**

---

### Post by Reeva on 2008-01-09
> **Caligatio said:**
> The underlying issue is the group isn't getting write permissions on the file.  Readd the create mask = 0660, directory mask = 0770, force group = users, and restart the server.  Then just try to create the file again and see what the permissions are.

For instance, my similiar share is:

[Private]
   comment = Family Only Share
   path = /path/to/files
   valid users = @family
   writeable = yes
   create mask = 0660
   directory mask = 2770
   force group = family

Thank you for your help. Now I get those filpermissions:
-rw-rw---- 1 marc users 859629 2007-12-14 10:37 anotherfile.txt

Now I can read and write/delete with all the members from the 'users' group.

The only thing is, when I use " force group = users " .. that It doesn't work. I can't get acces with a usergroup-member account ?

Thank you

---

### Post by geirha on 2008-01-09
What do you mean by "usergroup-member account"?

---

### Post by Reeva on 2008-01-09
> **geirha said:**
> What do you mean by "usergroup-member account"?

I mean an account, and this account is member of the group 'user'.

thank you

---

### Post by geirha on 2008-01-09
I'm not sure I understand what you mean. If you want users in the user group to be able to access as well, then you'd just add that group to valid users?

```
valid users = @users, @user
```

---

### Post by Reeva on 2008-01-09
> **geirha said:**
> I'm not sure I understand what you mean. If you want users in the user group to be able to access as well, then you'd just add that group to valid users?

```
valid users = @users, @user
```

I'm sorry, did not explained it well ..

the group is ' users ' .. which has some members.

when I use " force group = users " , I can't connect to the samba server anymore with the accounts from the users - group ..

Why is that?

---

### Post by Caligatio on 2008-01-09
Reeva,

Try this:

[gedeelde_server]
   comment = shared folder for all users
   path = /home/shares/sharefolder
   valid users =  @users
   read only = no
   create mask = 0660
   force create mode = 0660
   directory mask = 0770
   force directory mode = 2770

from the command line:
sudo chgrp -R users /home/shares/sharefolder
sudo find /home/shares/sharefolder -type d -exec chmod g+s {} \;

If you set the setgid bit on the folder that belongs to "users" all subsquent files/folders created will belong to the group "users"  The last command changes all the existing folders to support this functionality.

IMO, it's better to let the filesystem deal with permissions than SAMBA.

EDIT: Also make sure you can navigate like you expect using SSH or something.  If you can normally browse files, least that narrows the issue down to SAMBA as opposed to two places.  Also, ensure that everyone you think is in the users group is actually in the users group.

---

