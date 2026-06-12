---
title: "Recover deleted files from command line?"
date: 2015-07-06
forum: General Help
---

### Post by peter1897 on 2015-07-06
Is there a tool to recover deleted files that can do this:

Search for deleted file using wildcard like this: **sudo recover_command a* **
In this case it will search for deleted files that start with **a**.

After listing the found deleted files i want to be able the select a specific file and recover it, and not recovering all found deleted files.

---

### Post by Bashing-om on 2015-07-06
peter1897; Hi !

Short answer is no.

There are tools that might be able to recover a deleted file. 
See:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Upfront:
[INDENT][INDENT]can be a real problem
[INDENT][INDENT][INDENT][INDENT]when the bear eats you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by efflandt on 2015-07-08
Typically if you use a gui file manager to delete files, it moves them to Trash, and you can restore a file from there with the gui.

If you delete a file from the shell or shell script it is not saved anywhere and there is no command to undelete, which is why you would need to use file recovery tools (like testdisk or related photorec).

---

### Post by steeldriver on 2015-07-08
There's [extundelete](http://extundelete.sourceforge.net/) - I have not tried it myself

---

