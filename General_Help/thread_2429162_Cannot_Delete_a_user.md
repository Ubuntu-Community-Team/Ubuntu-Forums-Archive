---
title: "Cannot Delete a user"
date: 2019-10-14
forum: General Help
---

### Post by keystonecop on 2019-10-14
When trying to delete a users using the userdel command, we get this error:

Multiple entries named 'sudo' in /etc/gshadow. Please fix this with pwck or grpck.
userdel: failed to prepare the new /etc/gshadow entry 'sudo'

We have ran pwck and grpck but still have the same error after we try to delete the user once the complete.

When checking the /etc/gshadow file, there lots of enties fo sudo and other groups. 

Any one any ideas what we can do to fix this?

Its Ubuntu 14.04.06 that we are running.

---

### Post by HermanAB on 2019-10-14
Copy and paste the command and response that you ran, else we cannot comment on what went wrong.

---

### Post by keystonecop on 2019-10-14
Hi there,

Command to delete the user

userdel adminjustin
Multiple entries named 'adm' in /etc/gshadow. Please fix this with pwck or grpck                                                   .
userdel: failed to prepare the new /etc/gshadow entry 'adm'

When we run grpck, we get output like below:

'backupadmin' is a member of the 'adm' group in /etc/group but not in /etc/gshadow
'backupadmin' is a member of the 'sudo' group in /etc/group but not in /etc/gshadow


duplicate shadow group entry
delete line 'adm:*::syslog,mjk,adminchris,adminphilip,adminjustin'? 

When we run pwck, we get output like below:

no matching password file entry in /etc/shadow
add user 'username' in /etc/shadow?


When we try to run grpconv, we get the output below:


Multiple entries named 'root' in /etc/gshadow. Please fix this with pwck or grpck.
grpconv: failed to prepare the new /etc/gshadow entry 'root'

---

### Post by TheFu on 2019-10-14
I would used sudoedit on the files and manually make them consistent.

---

### Post by keystonecop on 2019-10-14
Thanks for the update on sudoedit.

In relation to resolving the gshadow issue, are yoou suggesting we manually edit this file using it?

Is there a way to recreate the gshadow file from the existing groups file perhaps?

---

### Post by TheFu on 2019-10-14
passwd, groups, shadow, gshadow are all just text files.  Any beginning Unix admin guide should explain what each field in each of those files means.  It isn't difficult for an admin to understand how the fields in each connect to the other files.  Just make them consistent.  Some software made those files inconsistent, somehow.  Probably through a script that didn't perform enough checking.  They are text-based databases.  The first column is the "key" and it must be unique in each file.

Make backups of any files BEFORE you change them - including the specific user, group, permissions and ACLs first.

sudoedit is just a smart front-end to any editor. You can edit anyway you like. If sudo doesn't work because the files are inconsistent, boot from an ISO/flash drive, mount the storage where /etc/ is and do the stuff above to fix it.

BTW, the manpages for each of these files also explains what each field is and perhaps how to make them consistent.

This isn't rocket science.  I would know.

---

