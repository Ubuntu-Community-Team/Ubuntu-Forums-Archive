---
title: "Backing Up Home Directory"
date: 2007-10-18
forum: General Help
---

### Post by Athanasius on 2007-10-18
I am using Edubuntu Gutsy and I have been having difficulty, not necessarily in backing up my /home partition, but when I format and reinstall the user account permissions are all messed up (there are about 9 user accounts).  It seems that the user id numbers are all off or something.  Are these kept in a separate directory that I should also be backing up along with /home?

---

### Post by dcstar on 2007-10-18
> **Athanasius said:**
> I am using Edubuntu Gutsy and I have been having difficulty, not necessarily in backing up my /home partition, but when I format and reinstall the user account permissions are all messed up (there are about 9 user accounts).  It seems that the user id numbers are all off or something.  Are these kept in a separate directory that I should also be backing up along with /home?

Userid number settings are not guaranteed to follow over with new installations, so you will experience issues like this.

The easiest way to fix this sort of thing is to create all the new User accounts on the new system, then (as root), go into each Home directory and set the Owner to the appropriate user for all the files and directories down each tree.

If an Upgrade is done, then this shouldn't be an issue, but a new install has no idea of the old credentials.

You **may** be able to fix things up by copying the following files from an old install to a new one, but be careful:

```
/etc/gshadow
/etc/shadow
/etc/passwd
/etc/group
```

---

### Post by Athanasius on 2007-10-18
I also have trouble doing that because when I change the ownership of a folder it won't apply the change to the files in the folder.

---

