---
title: "can see file using ls, but can't see the content using less"
date: 2016-03-23
forum: General Help
---

### Post by marchello_lippi2 on 2016-03-23
Hi all, 

I can see file using ls, but can't see the content using less. What does it mean and how to help? 
Thanks ahead.

---

### Post by sudodus on 2016-03-23
What file is it? How big is it?

Please post the output of the command

```
ls -l "file-name"
```

---

### Post by marchello_lippi2 on 2016-03-23
Well, this time it worked. 

ls -l /u01/t1/admin/ef/log/tr.txt
-rw-r--r-- 1 t1 oinstall 10120 March 23 17:10 /u01/t1/admin/ef/log/tr.txt

As I can see (if I do everything correct) the error happens from time to time somehow.
Will check later to catch the error and will update here.
Can you tell me what these rights -rw-r--r-- mean? 
Thanks.

---

### Post by ajgreeny on 2016-03-23
Those permissions
** -rw-r--r--**
are grouped in the following manner:-
The first - in your example shows this is a file, not a directory, it would show a d if it were.
The following nine characters are grouped in three lots of three, for owner, group and others.
The first group of three, the **rw-** is the permissions for the file owner and shows read/write but no execution permission.
The next two groups of three, each with **r--** show permissions for group and others in that order, with read only permission.

---

### Post by marchello_lippi2 on 2016-04-03
[**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=27747"), 
thanks.

---

