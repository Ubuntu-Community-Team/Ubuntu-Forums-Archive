---
title: "Changing Home Folder"
date: 2007-03-01
forum: General Help
---

### Post by rafaelperrone on 2007-03-01
I have a dual boot computer with winXP and ubuntu and i would like them to use the same place to save my files (Home and My Documents). SO i tried just changing my ubuntu home folder to /media/sdb5/documents t(hat is the folder my winxp uses to save my files but then i couldnt log in to ubuntu anymore and i had to manually edit my /etc/passwd file to be able to log again. Maybe its something to do with the folder's permissions.

How can I do it?

Yet, even if its not possible to share the same folder between winxp and linux, how can i just use another folder in that partition (/media/sdb/something)?

thanks in advance

perrone

---

### Post by mac.ryan on 2007-03-02
AFAIK, you cannot mount "/home" onto a filesystem that is not natively supported by Ubuntu (i.e. NTFS). I see two possible solutions:
[LIST=1]
[*]Create a new partition in Ext3 and mount /home there, then install the EXT drivers on windows and modify "my documents" in order to point  onto the right partition.
[*](Workaround) Changing your "home/username" directory into a soft link on the windows directory where your documents are.'[/LIST]

---

### Post by rafaelperrone on 2007-03-02
But the partition im trying to mount home on is a FAT32 partition (/media/sdb5 e a FAT32 partition). I think it has something to do with the folder's permissions.

What command should I use to do the soft link?

ln -s /home/rafaelperrone /media/sdb5/Documents/rafaelperrone


or

ln -s /media/sdb5/Documents/rafaelperrone /home/rafaelperrone

???

Thanks a lot.

---

### Post by Ramses de Norre on 2007-03-02
FAT doesn't support permissions, you'll get into trouble soon when mounting /home on a fat partition.
I think it's quiet impossible to do what you want. You can however put all stuff like images and music on the fat and make symlinks to it from your home directory.

---

### Post by mac.ryan on 2007-03-02
> **rafaelperrone said:**
> What command should I use to do the soft link?

Example:
I want to see my M$ "foodirectory" appearing in my linux /home/username directory. I would do (but there are different methods:

```
cd /home/username
ln -s /media/sdb5/Documents/rafaelperrone/foodirectory
```

The answer from Ramses is the same as my initial "2 (workaround)". "Symlink" or "symbolic link" is the same as "soft links".

As a completion to my "solution 1", I should add that EXT drivers for windows do not support file permissions either (i.e. all of the files on a given EXT partition will be accessible by any user under windows.

---

### Post by rafaelperrone on 2007-03-02
Ill try the symlink later when I get home.

Thanks a lot.

---

