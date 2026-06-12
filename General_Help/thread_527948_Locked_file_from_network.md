---
title: "Locked file from network"
date: 2007-08-17
forum: General Help
---

### Post by Pete_uk on 2007-08-17
Hi everyone, first post!

I have Ubuntu on VM wear virtual server. I dragged my IE favourites folder from Windows XP onto my Ubuntu desktop to convert and use in Firefox. The problem is this file has a lock on it so I don’t have permission to delete it. Any help would be appreciated! 


Pete   
:(

---

### Post by jamvegan on 2007-08-18
You may need to change the file ownership.  To find out, right-click the file and select Properties.  Then click the Permissions tab.  If the Owner listed at the top is not you, then do the following:
 
Open a terminal (Applications->Accessories->Terminal).  Navigate to the appropriate directory.  You say that you dragged it to your desktop, so you can do this by typing
```
cd Desktop/
```
Then type the following command:
```
sudo chown -R $USER: filename
```
where you replace "filename" with the actual name of the file or folder.  You will be prompted for your password, and then you should be able to delete the file.

---

