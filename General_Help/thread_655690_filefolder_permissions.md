---
title: "file/folder permissions"
date: 2008-01-01
forum: General Help
---

### Post by rkk on 2008-01-01
Hi. I need some help please. I just started using Ubuntu this summer, but I am stuck. I set up a Linux box for a file server. Got Samba going, can log in, etc. My problem is, when ever a new file is made, and save to the shared folder, it has the owner and group as the person who made the document. The owner can read and write, the group is read only, others have none. I want to automatically inherit the permissions of the parent folder, so they can be read&write to the group users. I have tried everything. Thanks. Something simple please!

---

### Post by jken146 on 2008-01-02
You'll need to change the permissions of these files.  The command is chmod.  See its man page for more details ```
man chmod
```


[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by p_quarles on 2008-01-02
The specific command you want would be like this:
```
sudo chmod g+s /path/to/samba/share
```
This will cause any further files created in that directory to be owned by the group rather than the user that created it.

---

