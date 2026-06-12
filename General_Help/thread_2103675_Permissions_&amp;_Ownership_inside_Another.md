---
title: "Permissions &amp; Ownership inside Another"
date: 2013-01-10
forum: General Help
---

### Post by Xaotique on 2013-01-10
I have a folder that contains a few different folders.  I want to use VSFTPD and let users edit/delete/add files in each of them folders, but only their folder.

So, with 775 permissions and ownership under my name, I can log on with FTP under another user and view the files.  I cannot edit/rename/delete/add files though.

When I try to use 777 or change ownership of the folder and contents to theirs, then I can't even connect.

These folders are in a subfolder of my home.  I'm assuming since vsftpd is running from me, is why I can't change the ownership to them and allow them to view it.  I don't know why 777 permissions would stop connection though.  I need them to be able to modify these files.

Please, any help is appreciated.

PS: I already have the user set up with a password and their home set to their correct folder.  They can see the files, but can't do anything with them.

// edit: When I set the contents of their folder (subfolders and files) to 777 they can still view the files, but still can't modify them?

---

### Post by Xaotique on 2013-01-10
Okay .. this bothers me.  I finally asked for help and figured it out.  In the vsftpd config file, I had write permissions off.  Now when I set chown to their user, it works fine.

For some reason, explaining my problem always helps me figure things out. :/  Sorry for pointless thread.

---

