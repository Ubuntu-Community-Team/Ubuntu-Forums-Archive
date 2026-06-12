---
title: "File &amp; Folder Permission Inheritance"
date: 2017-01-13
forum: General Help
---

### Post by fastenedrex on 2017-01-13
Hello, 

I'm trying to set up inheritance for parent directory "somedir". Currently "somedir" is assigned permission 770 with owner "user" and group "group". I need the permission 770 and group "group" to be assigned to every file and directory that has been, and will be created within "somedir".

Any ideas?

---

### Post by Keith_Helms on 2017-01-13
I believe you can do that using Access Control Lists, but not with regular permissions.

---

### Post by bab1 on 2017-01-13
> **fastenedrex said:**
> Hello, 

I'm trying to set up inheritance for parent directory "somedir". Currently "somedir" is assigned permission 770 with owner "user" and group "group". I need the permission 770 and group "group" to be assigned to every file and directory that has been, and will be created within "somedir".

Any ideas?

You can set group inheritance by setting the SGID bit on group permissions at the top of the file system branch in question (chmod 2770).

---

