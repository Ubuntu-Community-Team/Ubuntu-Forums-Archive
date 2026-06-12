---
title: "Remove permission to delete folder, but not files"
date: 2014-03-29
forum: General Help
---

### Post by GigabyteProduction on 2014-03-29
I have a samba share with a folder called Sandbox that i want to allow guests to be able to write to. Sandbox is the only folder i want guests to write too, and the permissions for everything else is already set to readonly for 'other'. But if i set the everything permissions on Sandbox, anyone will be able to write to it, **and delete the folder itself**. **i don't want anybody to be able o delete the Sandbox folder**. If i put the sticky bit on the folder, it makes it so the files that are uploaded by guests aren't deletable by anybody but the guest, even if the files that are uploaded are forced to have everything permissions.

How can i allow **files from within the Sandbox folder to be deletable by anybody** but **prevent anybody from deleting the Sandbox folder**?

---

### Post by GigabyteProduction on 2014-03-29
Well i was able to get what i want but at too much of a literal sense... I have the Sandbox folder owned by root, but with the permissions of rwxrwxrwx, the folder can't be deleted by anybody other than root, but files inside of it can be delted by anybody despite who created it. So if i dropped a file in there, i will own it, and i set the permissions to rw-r--r--, the literal nobody user is allowed to delete it. The same goes for if the file was owned by root, and the only way to not allow deleting is to have a file's permissions be read only, even for the owner. So i was truely able to make an anything goes folder, and even though i didn't say it, i didn't want the files that are owned by legitimate users to be deletable. So now i'm trying to think about a setup using ACL where a file owned by nobody can be deleted by a regular user like me, but not allow the opposite... I don't like linux's permission system so much...

---

### Post by Impavidus on 2014-03-30
I don't know too much about samba, so I could be wrong, but on Linux to have permission to delete (or create) files or directories you need write permission on the parent directory. The permissions or owner of the file or directory to be removed are irrelevant, with two exceptions:
- in case of removing a directory you also need permission to remove all it's contents, if any.
- if the sticky bit on the thing-to-remove's parent directory has been set, the thing-to-remove must be owned by you.
So the sandbox directory can't be deleted whatever it's permissions are and setting a file to read only can't prevent it from being deleted. But I'm not sure what exactly you want.

---

### Post by steeldriver on 2014-03-30
... it sounds like you need the SAMBA equivalent of the **setgid** bit rather than the **sticky** bit - I'm sorry, I don't know enough about SAMBA to know more than that but perhaps it will give you a better term to search on

---

