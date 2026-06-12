---
title: "Setting Permissions on Samba Share"
date: 2007-10-10
forum: General Help
---

### Post by raymond3 on 2007-10-10
I have a directory (/home/common) that I want everyone to have read/write access to.  I also want everyone to be able to read/write/delete/rename everyone else's documents and folders in this directory.

Right now I have this in smb.conf

[users]
	comment = All users
	path = /home
	read only = No
	inherit acls = Yes
	veto files = /aquota.user/groups/shares/

I want to make sure that the users home directories can't be accessed by anyone else but have full access to the common directory (that's located in /home).

How can I do that and maintain the samba path (//server/users/common/)?

---

### Post by raymond3 on 2007-10-10
I changed it to this:

[users]
	comment = All users
	path = /home
	read only = No
	public = Yes
	inherit permissions = Yes

and set the permissions on /home/common to allow read/write/execute for everyone.  This seems to work.  Are there problems with doing this?

---

