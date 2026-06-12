---
title: "Create ACL and maintain inherited permissions for all new files"
date: 2018-06-07
forum: General Help
---

### Post by billybobjay on 2018-06-07
Hi, 

I am attempting to create a new user to have the ability to check all folders within our sftp structure, we have multiple sftp users that have single user to folder permissions.  The goal is to have one user be able to access each of these folders using the ACL's and have read, write and execute permissions well still maintaining inherited permissions for when a new file is uploaded.  I have tried the following-

[COLOR=#111111][FONT=Ubuntu]setfacl -d -m g::rwx /folder_location

Yet it does not retain the ACL for the new file uploads or when files are created further down the folder structure.


Thanks, 


[/FONT][/COLOR]

---

### Post by billybobjay on 2018-06-07
To add to this, after some further reading it looks like ACL's work for new files but do not transition over to copied files, to work around this I created a crontab script to set the acl's again every so often, so far it has been working good.  Any thoughts though would be appreciated.

Thanks,

---

