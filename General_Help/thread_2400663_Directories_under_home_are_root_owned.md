---
title: "Directories under home are root owned"
date: 2018-09-08
forum: General Help
---

### Post by raleigh3 on 2018-09-08
I have a lot of directories under my home directory that are root owned.

Is that normal?

I noticed it after grsync was not able to backup some files.

---

### Post by vanadium on 2018-09-08
Not normal, and indeed, some havoc was created at some time. Change the ownership of the files in your home folder back to your own. You can achieve this easily with a command. You could do at once for your entire home folder, but it could be safe to do it more selectively only for the files where you see a problem. For example
```

sudo chown -R $USER:$USER ~/Documents

```

will return ownership of your Documents folder and its contents (the -R option implies: operate on all files and folders within the listed folder) to the user running the command (the contents of the variable $USER, i.e., your login, will automatically be substituted).

For sure, any user data within Documents can be owned by yourself. However, be carefull in general with changing ownership and permissions, and never perform this "in bulk" in system directories.

---

### Post by raleigh3 on 2018-09-08
Thanks.

I just changed owner for directories under home.

---

