---
title: "Not able to create New folder in partitions I created. Option grayed out."
date: 2018-12-01
forum: General Help
---

### Post by vigisbig786 on 2018-12-01
Hi,

I am not able to create new folder neither paste files in any of the partition I created. What have I done wrong. "New folder" and 'Paste" grayed out.

PS: I am a new user. I don't know much about Linux/Ubuntu. 

Regards,
Pankaj

---

### Post by SeijiSensei on 2018-12-01
Start with learning about file permissions:  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Impavidus on 2018-12-01
Probably a permission issue. Permissions are central in Linux security. What type of partition is this? When you create a new ext4 partition, it's owned by root and only root can create anything on that partition.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Dennis N on 2018-12-01
You should make yourself owner of the newly created partition's file system. The owner has all the rights needed to use the partition.

Example: Suppose a partition is being mounted at **/mnt/myfiles** on startup through an entry in **/etc/fstab**.  

Once mounted, run in terminal (substitute your actual username where shown):
```
 sudo chown -R username:username /mnt/myfiles
```
This only needs to be done once. Any added files and folders also will belong to you.

---

### Post by yancek on 2018-12-01
To add to the previous comments, Ubuntu like all Linux systems, is designed as a multi-user system.  That means that a normal user has read/write access to only the /home/user directory and sub-directories and you will need to change ownership and/or permissions on the various partitions.  Are these all Linux filesystems or do you have windows filesystems on some?

---

### Post by ajgreeny on 2018-12-01
Also tell us how you created those partitions, which might give us a clue about why you have this problem.

I do, however, suspect a permissions problem as suggested above.

---

### Post by vigisbig786 on 2018-12-02
> **Dennis N said:**
> You should make yourself owner of the newly created partition's file system. The owner has all the rights needed to use the partition.

Example: Suppose a partition is being mounted at **/mnt/myfiles** on startup through an entry in **/etc/fstab**.  

Once mounted, run in terminal (substitute your actual username where shown):
```
 sudo chown -R username:username /mnt/myfiles
```
This only needs to be done once. Any added files and folders also will belong to you.

Thanks. I will try what you suggest. Also, is there a way this can be done through GUI? I am not very comfortable with using terminal.

---

### Post by vigisbig786 on 2018-12-02
Thanks for reply. The hard disk was formatted and all partitions are freshly created in Ubuntu during setup.

---

### Post by ajgreeny on 2018-12-02
Partitions created during installation will be ext4 unless you manually created them and used another format type.

Those ext4 partitions will also all be owned by root with the exception of your home partition (if you created one) which will of course be owned by you as user.
The command ```
sudo chown -R $USER:$USER mountpoint/of/partition
``` as shown above will make you, as user, owner of the partition.

---

### Post by vigisbig786 on 2018-12-02
> **ajgreeny said:**
> Partitions created during installation will be ext4 unless you manually created them and used another format type.

Those ext4 partitions will also all be owned by root with the exception of your home partition (if you created one) which will of course be owned by you as user.
The command ```
sudo chown -R $USER:$USER mountpoint/of/partition
``` as shown above will make you, as user, owner of the partition.

Thanks, it solved the problem! :-)

---

### Post by ajgreeny on 2018-12-02
Great news! 

Please mark as **SOLVED** from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

