---
title: "unlock /opt/gns3/projects folder so that i can update file using GUI instead of CLI"
date: 2013-05-13
forum: General Help
---

### Post by trojanworrier on 2013-05-13
currently /opt/gns3/projects folder is locked so file in this folder can only be updated using CLI "sudo" commands and using GNS3 application (this folder belongs to GNS3 app). how to unlock this folder so that I can update files in this folder using gedit or GUI instead of going to CLI or GNS3 app each time I want to edit this file.

---

### Post by redmk2 on 2013-05-14
> **trojanworrier said:**
> currently /opt/gns3/projects folder is locked so file in this folder can only be updated using CLI "sudo" commands and using GNS3 application (this folder belongs to GNS3 app). how to unlock this folder so that I can update files in this folder using gedit or GUI instead of going to CLI or GNS3 app each time I want to edit this file.

You can change the group ownership or add yourself to the group that owns the directory or files.  What are the owner/group and permissions from /opt to  /opt/gns3/projects ?

I have tree installed so I would just use this command to see all the permissions along the entire path```
tree -p  /opt/gns3/projects
```

You can install tree with this command```
sudo apt-get update; sudo apt-get install tree
```

---

