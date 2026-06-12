---
title: "Make new file permission inherit from the parent directory?"
date: 2016-05-30
forum: General Help
---

### Post by alka5eltzer on 2016-05-30
Hi all,

I Have a Directory called /home/Projects
Say a user creates a new directory within /home/Projects

e.g. /home/Projects/NewDirectory

It always ends up as read only????

This is from the Conf File:

[Projects]
writeable = yes
path = /home/Projects
write list = shay,Paul,Brian,Eamonn,Joe,Trevor,Tracy,Colin,caro l,David,Mark,PaulS,Terry,@users
force directory mode = 777
force create mode = 777
valid users = shay,Paul,Brian,Eamonn,Joe,Trevor,Tracy,Colin,caro l,David,Mark,PaulS,Terry,@users
create mode = 777
directory mode = 777

How do I make make new file permission inherit from the parent directory?

Thanks in advance

---

### Post by QDR06VV9 on 2016-05-30
Just add the -R option to recursively change the permissions of files. An example, recursively add read and write permissions for the owner and group on foldername:

```
chmod -R ug+rw foldername
```

Permissions will be like 664 or 775.

**Setting the permissions to 777 is highly discouraged.** You get errors in either Apache or your editor regarding permissions because apache runs under a different user (www-data) than you.

If you want to write to /var/www, add yourself to the www-data group and set umask+permissions accordingly.
Hope this makes sense and is useful.
Regards

---

### Post by SeijiSensei on 2016-05-30
If all the valid users belong to the same Unix group, then you can add "force group = groupname" to the Samba configuration.

---

### Post by alka5eltzer on 2016-05-31
> **runrickus said:**
> Just add the -R option to recursively change the permissions of files. An example, recursively add read and write permissions for the owner and group on foldername:

```
chmod -R ug+rw foldername
```

Permissions will be like 664 or 775.



This worked perfectly for me... like a charm :D Thanks so much for your help guys

---

### Post by QDR06VV9 on 2016-05-31
Very Nice glad it worked out for you..and thanks for marking it as Solved.
Kind Regards

---

