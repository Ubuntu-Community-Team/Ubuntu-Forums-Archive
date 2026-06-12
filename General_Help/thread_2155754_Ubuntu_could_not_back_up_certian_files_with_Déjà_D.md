---
title: "Ubuntu could not back up certian files with Déjà Dup Backup?"
date: 2013-06-19
forum: General Help
---

### Post by garyzw on 2013-06-19
Ubuntu could not back up the following files when using Déjà Dup Backup

/home/gary/.cache/dconf
/home/gary/.gvfs

How to fix?

---

### Post by 2F4U on 2013-06-19
Those "." files are usually not supposed to be backed up, since they contain either temporary information or configuration information. If you absolutely want them, make sure that no process writes on them during backup. Else exclude them from the backup.

---

### Post by garyzw on 2013-06-19
> **2F4U said:**
> Those "." files are usually not supposed to be backed up, since they contain either temporary information or configuration information. If you absolutely want them, make sure that no process writes on them during backup. Else exclude them from the backup.

Strange I added them to be excluded but I still get the message that it could not back up those files 


[ATTACH=CONFIG]243963[/ATTACH]

---

### Post by victor9098 on 2013-06-19
Been getting the same problem myself since a fresh install last week, its the first time I have seen this error with Deja Dup. Going to double check the permissions and see if the error still occurs

---

### Post by victor9098 on 2013-06-19
In my case the folder permissions had been changed to root, I changed them back to me, ran a backup and there was no error report.

---

### Post by garyzw on 2013-06-19
> **victor9098 said:**
> In my case the folder permissions had been changed to root, I changed them back to me, ran a backup and there was no error report.

I think that is my problem also-- could you please post the commands to change the folder permissions for those files?
Thanks

---

### Post by victor9098 on 2013-06-19
The way I did it is probably the long way, but worked for me.

I opened a terminal 
Typed "gksudo nautilus" 
Navigated to computer -> home -> [username]
"ctrl+h" to show the hidden files
Right clicked on each of the offending folders, went into the permissions tab changed the Owner and Group to my username, checked the box to apply permissions to enclosed files.
*[EDIT: Terminal crashed after I changed the owner permissions, but just navigating to the folders after the crash found that the change had worked and I could then change the Group setting]*
Closed out, exited terminal, ran backup and no more errors.

Hope that helps!

---

