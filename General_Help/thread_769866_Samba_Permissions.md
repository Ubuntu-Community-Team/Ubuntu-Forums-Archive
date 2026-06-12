---
title: "Samba Permissions"
date: 2008-04-26
forum: General Help
---

### Post by shthap3ns on 2008-04-26
Hi all,

I'm setting up my /etc/samba/smb.conf file.

Here's how it currently looks:
[public]
   comment = Public Folder
   path = /home/shares/public
   valid users = @users
   force group = users
   create mask = 0660
   directory mask = 0771
   writable = yes

[shares]
   comment = all user access
   path = /home/shares
   valid users = @blah
   force group = blah
   create mask = 0660
   directory mask = 0771
   writable = yes

[homes]
   comment = Home Directories
   browseable = yes
   valid users = %S
   writable = yes
   create mask = 0700
   directory mask = 0700

I've set the default home directory for each user to be: /home/shares/users/<username>. The 'shares' directory with the usergroup 'blah' is meant for an "admin" user, who can see the folders /public and /users in the /home/share directory. 

Thing is, the "admin" user "blah" can't access any of the files in the "users" directory. It can see the files, but has no read/write access to it. What do I need to do?

Thanks for any suggestions!

---

### Post by rbmorse on 2008-04-27
If I understand correctly...what I did is create a new group (shares) and then make user blah a member of the group shares. I then changed the group ownership of each share to "shares" (i.e., sudo chgrp -R shares *foldername*)

---

