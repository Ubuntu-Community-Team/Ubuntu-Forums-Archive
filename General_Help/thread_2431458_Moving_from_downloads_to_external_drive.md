---
title: "Moving from downloads to external drive"
date: 2019-11-16
forum: General Help
---

### Post by b1jqxk44 on 2019-11-16
I just bought a 2 TB SSD to put movies on. I've been copying and pasting to the 2 TB drive and it's been working great, for about 5 days.
Now I'm getting error, You do not have permission to create it in this destination. 
How do I fix this problem? Is there a command line too fix this. 
I still need to transfer 1.6 TB from my downloads to the external drive to save them, and make space on my internal drive.
How is this done, 
Thanks in advance b1.

---

### Post by TheFu on 2019-11-16
Start here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Hopefully, you formatted the drive to use ext4 BEFORE starting the copies.

And it is always necessary to check the system log files for any errors or warnings.  New HDDs fail between 0.5% and 2% of the time in the first month.

---

### Post by b1jqxk44 on 2019-11-16
The drive is ext4, I redid the file permission to make sure they were on r, w, x and 
I,m still getting the same error.  You do not have permission to create it in this destination. 
I have a feeling this drive is damaged.

---

### Post by TheFu on 2019-11-16
Best to show the **full permissions** for the directory, parent directory and a few files.  Need to see the owner, group, and ACLs.

```
ls -al /path/to/the/mount
```

for the directory, please. Post using _code tags_ so things line up correctly.

---

### Post by croyle on 2019-11-16
I've run into this problem my self check the formatting of the drive some formats only allow 4GB file sizes FAT32 and if you tried to move 2TB and got error when 1.6 was left sounds like you hit the wall.
Jason

---

