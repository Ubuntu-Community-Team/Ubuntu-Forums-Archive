---
title: "/etc share permissions"
date: 2013-04-01
forum: General Help
---

### Post by roe74979 on 2013-04-01
Hello all,

I need to configure permissions to share a file in /etc.  the file does NOT have to stay in /etc, its jsut where I put it.  So if anyone knows another file I can out it in and have an easier time sharing please let me know.  But I do not know how to edit the share permissions in terminal, and it wound not let me do it if I right click and go to permissions.  

anyone have a code that might help?

thanks!

---

### Post by deadflowr on 2013-04-01
How do you want to share it?
Locally, or over a network.
If locally, and I mean where one computer is shared by others, then run
```
sudo chmod 777 the filename
```
This will give anybody full-rights to the file, whether they be the owner, in the files group, or simply other.

If over a network, create a folder and enable sharing, and share the folder. Then place the file there.
To enable sharing, right-click on the made folder and go to sharing options then follow the various steps to get sharing working.

---

### Post by roe74979 on 2013-04-01
this will be sharing via Samba to 1 PC for now.  so i'll fun that code and see what happens

thanks for the responce

---

### Post by roe74979 on 2013-04-01
the code was PERFECT!  thank you SOOO much for the help!  :D

---

