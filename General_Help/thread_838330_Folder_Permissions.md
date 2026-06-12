---
title: "Folder Permissions"
date: 2008-06-23
forum: General Help
---

### Post by ifoam on 2008-06-23
I'm setting up an sftp and want one folder where people can add and remove files.

I want the group "sftp" to have read and write access to /home/sftp (this is not a home folder, just located there).

How can I do this so that any new files as well (uploaded by either user) can be rw to both users?

---

### Post by lanzailan on 2008-06-23
:-k:-k

---

### Post by Halfling Rogue on 2008-06-23
Near as I can tell, you just right-click on the folder (while logged in as whatever user you used to create the folder), then go to the Permissions tab, set the Group to sftp, and set Folder Access to "Create and delete files". And if you have anything in the folder already, click "Apply changes to enclosed files", too.

---

