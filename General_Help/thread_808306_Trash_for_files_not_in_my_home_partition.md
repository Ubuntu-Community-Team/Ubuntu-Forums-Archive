---
title: "Trash for files not in my /home partition?"
date: 2008-05-26
forum: General Help
---

### Post by leenwebb on 2008-05-26
Hi all,
I have my drive in three partitions:  one for /home, one for /var, and one for everything else.  When I delete something from /var (where I do most of my work), I am informed that "this is really getting deleted, because there's no trash here".  I gather that Trash (because it exists in /home) can't hold things from other partitions.

Is there a way to set up a Trash for my /var partition?  I am constantly pulling things out of the trash a day or two after I delete them.  It hasn't happened yet that I really need a key file from /var that I've deleted, but it's bound to.

Can I somehow allow my deleted /var files to go to my /home trash, or can I set up a separate /var trash?

Many thanks,
Eileen

---

### Post by mbarak on 2008-05-26
try dragging and dropping the files to the trash ban (bottom right corner)

---

### Post by sisco311 on 2008-05-26
Maybe you don't have permission to create a folder in /var? 

try to create a .Trash-<user-id> folder:
```
sudo mkdir /var/.Trash-`id -u`
```and set the correct permissions on the folder:
```
sudo chown -R $USERNAME:$GROUPNAME /var/.Trash-`id -u`
```

---

### Post by chrisccoulson on 2008-05-26
What you actually need to do is create a '.Trash' folder at the root of the partition and give it 1777 permissions (sticky bit set and rwx permissions for everyone). When you delete a file in Nautilus, it checks for the existense of this folder, then checks that you can write to it, and then checks the sticky bit is set. If all of the checks pass, it creates a sub-folder named according to your user ID in which it stores your trash.

Using this method, trash will work automatically for all users on your system without having to manually create a trash folder for each user. In your case, to do this:
```
sudo mkdir /var/.Trash
sudo chmod 1777 /var/.Trash
```

---

### Post by leenwebb on 2008-05-26
Perfect, chriscoulson, thank you!  That is exactly what I was looking for -- it even groups my /home trash and my /var trash in the same place (go > trash), so I don't have to look in multiple places for my files.

---

