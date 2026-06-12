---
title: "gedit won't save without directory permisson"
date: 2014-10-15
forum: General Help
---

### Post by chopra on 2014-10-15
Hi all,

I've run into a strange problem with gedit.  It usually works fine, but there's a file I own (and have full read and write priveledges to), but it is in a directory where I do not have write permission.  The problem is that, gedit will not let me save changes to the file, because it can't make a backup. Obviously, creating the backup file with the ~ isn't possible without write permission to the directory, but this shouldn't stop me from making changes to my own file.  I get this:

Could not create a backup file while saving /dir/file

gedit could not back up the old copy of the file before saving the new one. You can ignore this warning and save the file anyway, but if an error occurs while saving, you could lose the old copy of the file. Save anyway?

However, when I hit save, the message just reappears.  This is something that seems to be specific to my user account, because other users don't have the same problem.  

Forgot to mention, this is on Ubuntu 12.04 LTS

Chopra

---

### Post by yancek on 2014-10-15
Whether you can create, rename and delete a file does not depend on the  ownership and access rights of the file but of those of the parent  directory.

Just prefix gedit with sudo.

---

### Post by chopra on 2014-10-15
> **yancek said:**
> Whether you can create, rename and delete a file does not depend on the  ownership and access rights of the file but of those of the parent  directory.

Just prefix gedit with sudo.

I could do that, I suppose, but I shouldn't have to. The problem I'm facing clearly means that gedit is not configured properly for my account, which is why I posted this.  A text editior should allow me to modify the file, even if it doesn't have permission to create backups.  Emacs will still save modifications, for instance, it just gives me a message that it can't create a backup. Vim and nano both allow file modifications.

As I said, this is something specific to my primary user account.  I created a toy account, and with that account, all that is needed is file permissions, not directory permissions, with gedit.

Chopra

---

### Post by Impavidus on 2014-10-15
You can disable the backups in gedit, somewhere in the gedit preferences. I don't have gedit installed here.

---

### Post by chopra on 2014-10-15
> **Impavidus said:**
> You can disable the backups in gedit, somewhere in the gedit preferences. I don't have gedit installed here.

Aha! That was it.  Edit -> Prefrences -> Editor  and then uncheck 'create backup'.

Thanks.  Too bad it's not sophisticated enough to temporarily disable that on its own in those conditions, like emacs is, but oh well.  At least I know the source of the problem.

Chopra

---

