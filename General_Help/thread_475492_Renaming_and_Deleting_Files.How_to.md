---
title: "Renaming and Deleting Files.How to?"
date: 2007-06-16
forum: General Help
---

### Post by dimitar1995 on 2007-06-16
Hello.

First I wanna say hello becouse this is my first post.Ok,let's see my problem.

When I try to write,delete or rename files in /opt I get an error message that says that I don't nave the permisions.If there are solutions please tell me becouse I really need this.

Thanks.

---

### Post by wpshooter on 2007-06-16
I believe the /opt is part of the O/S.  Why would you be attempting to either delete or rename anything there ?

---

### Post by mikewhatever on 2007-06-16
Press Alt+F2 and type 'gksudo nautilus', enter your password and navigate to the directory in question. Delete and rename whatever necessary, but be very very careful.

---

### Post by dimitar1995 on 2007-06-16
Ok,Thanks...but with this command I can only delete files.I want to have perminitions to write,rename and delete.I need this becouse I've installed XAMPP,and I need to write,rename and delete some files.

---

### Post by dimitar1995 on 2007-06-16
Do you have other solutions ?:(

---

### Post by mikewhatever on 2007-06-17
If you have the permission to delete a file, that means you have the write permission for the directory, which should include renaming files. If you want to write to a specific file, add or delete lines etc, try the following in the terminal:
> gksudo gedit /opt/full_path_to_the_file

---

