---
title: "Moving Home Folders?"
date: 2007-01-24
forum: General Help
---

### Post by erkker on 2007-01-24
I just had a post answered about lossing my permissions when adding a new user and deleting the orignal user.  Thanks

But...

I have now created a new user with admin permissions and I want to delete the old (original) admin user, but I want to move my files, music, docs etc to the new home folder.  I figured out how to move them from the terminal as root.  However I want the new user to have read and write abilities. What little tidbit am I missing?

Thanks


-E

---

### Post by ewankho on 2007-01-24
Maybe you can change the permissions on the files or set the owner of the files to the new user.

---

### Post by lswb on 2007-01-25
Read up on the 'chown' command to find out how to set the user & group of the moved files to the user & group of the directory you moved them to. The chmod command will set permissions, you may need to use them both to get the combination you desire.

If the original files are readable by the new user, it can be quicker to copy the files (using cp) rather than move them (mv), then delete the originals. A copied file will have uid,gid, & permissions set to the default of the copier; a moved file will bring those attributes along with it.

---

