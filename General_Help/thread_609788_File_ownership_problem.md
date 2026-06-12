---
title: "File ownership problem"
date: 2007-11-11
forum: General Help
---

### Post by Athanasius on 2007-11-11
There are users' folders in the home directory (naturally).  Within a certain user's directory are folders that I put there from another user's directory - resulting in a folder that the present user cannot access.  I want to change the user of the sub-folder (not share or anything like that) to the owner of the directory.

I attempt to accomplish that by doing the following: Using the command "gksudo nautilus"  I navigate to the home directory.  Going to the user's folder I right-click on the sub-folder of whose I want to change.  I select the permissions tab, change the name  of the owner and then click "apply permissions to enclosed files".   

I am thinking that the ownership of those files should be as I set them but they are not and I must do this individually for all files in that folder.   What am I doing wrong?](*,)

---

### Post by archivator on 2007-11-11
You could do ```
sudo chown -R <user>:<group> folder/
``` where <user> is the new owner and <group> is the new owner's group. The -R stands for recursive, meaning it will apply these settings to anything inside folder/ .

---

### Post by Athanasius on 2007-11-11
Good, it worked, thanks!

---

