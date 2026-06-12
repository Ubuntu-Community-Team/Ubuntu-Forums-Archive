---
title: "Run bash automatically without prompt"
date: 2016-07-11
forum: General Help
---

### Post by 4kh3RAm on 2016-07-11
I have some bash scripts on my desktop.

Can I have them run instead of getting the this prompt ?

> Run In Terminal Display Cancel Run

---

### Post by TheFu on 2016-07-11
a) Do the permissions have the **execute bit** set for the owner and is the owner your userid?  If that doesn't work, ....
b) perhaps creating a **script.desktop** file for each script is needed?  There are examples on the system. The **locate** command will be able to find some or use **find**

Sorry my answer isn't 100% certain. Don't really use a desktop myself.

---

### Post by 4kh3RAm on 2016-07-11
> **TheFu said:**
> a) Do the permissions have the **execute bit** set for the owner and is the owner your userid?  If that doesn't work, ....
b) perhaps creating a **script.desktop** file for each script is needed?  There are examples on the system. The **locate** command will be able to find some or use **find**

Sorry my answer isn't 100% certain. Don't really use a desktop myself.

How do I check if the execute bit is set ?

---

### Post by yancek on 2016-07-11
Run ls -l from the Desktop directory if that is where the file are.  Should show output similar to below with the x's.  Or do ls -l Desktop to get the output for all files.  Check the user also.

> ls -l script.sh
-rwxr-xr-x 1 user users 472 Nov 27  2011 script.sh*


---

### Post by 4kh3RAm on 2016-07-12
For my script.

> -rwxrwxr-x 1 andy andy    886 Jul 11 20:59 BACKUP_AMD


---

### Post by TheFu on 2016-07-12
> **4kh3RAm said:**
> How do I check if the execute bit is set ?

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) . File and directory permissions are at the center of all Unix security. This is a basic, required, skill to have.

Based on a later post, it appears you'll need to create a .desktop file for each script.

---

