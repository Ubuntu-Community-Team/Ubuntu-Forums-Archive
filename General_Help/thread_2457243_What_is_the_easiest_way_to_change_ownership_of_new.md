---
title: "What is the easiest way to change ownership of new USB drive ?"
date: 2021-01-28
forum: General Help
---

### Post by helen314 on 2021-01-28
What is the easy way to change ownership of new USB drive ?
Since I am not the owner I cannot change permissions to copy files into new USB drive, or any drive.

I did try chown but it is geared to change  ownership with files. 

I am not looking for explanations why I have to do this, I just want an easy way to get access to new drives.

I am open to suggestions.

---

### Post by Dennis N on 2021-01-28
My best suggestions:
Insert the new drive, then use gparted to unmount it and do the following: Create a new partition table - GPT is best. Create a new partition. Suppose the new partition is sdb1. Format the partition. Assuming for Linux use it was formatted ext4, give it a label - this command will label it 'data':
```
sudo e2label /dev/sdb1 data
```
Quit gparted, remove and reinsert the drive, it will mount at /media/username/data where 'username' will be your user name.  
The command
```
sudo chown -R username:username /media/username/data 
```
will give you ownership and full access to the drive through this mount point in your root file system.

Enjoy your new USB drive.

---

### Post by TheFu on 2021-01-28
The file system determines what can and cannot be done.  "Drives" don't have owners, BTW.  Directories and files do.

---

