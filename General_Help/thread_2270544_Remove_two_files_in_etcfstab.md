---
title: "Remove two files in /etc/fstab"
date: 2015-03-23
forum: General Help
---

### Post by mountainman70 on 2015-03-23
I have two files in the etc folder called (fstab.save and fstab.save.1). I need to remove or delete these two files. How do I do this. I tried gksu gedit rm /etc/fstab.save and gksu gedit rm /etc/fstab.save.1, but neither worked. What would be the correct command to remove these files?

---

### Post by Dennis N on 2015-03-23
open terminal and cd to /etc
in the terminal, execute the command:
```
sudo rm fstab.save fstab.save.1
```

---

### Post by Keith_Helms on 2015-03-23
A little background information for future reference:

gksu(do) is used to invoke a graphical program as the superuser.
sudo is best used to invoke a command line program as the superuser (although it works on graphical programs too)
gedit is a graphical program for editing text files.
rm is a command line program for removing files or directories

so.....
when you were doing "gksu gedit" you were opening a text editor as the superuser.  Executing "gksu gedit rm /etc/fstab.save" tries to open files named "rm" and "/etc/fstab.save" in the text editor.

---

### Post by mountainman70 on 2015-03-23
> **Dennis N said:**
> open terminal and cd to /etc
in the terminal, execute the command:
```
sudo rm fstab.save fstab.save.1
```

> **Keith_Helms said:**
> A little background information for future reference:

gksu(do) is used to invoke a graphical program as the superuser.
sudo is best used to invoke a command line program as the superuser (although it works on graphical programs too)
gedit is a graphical program for editing text files.
rm is a command line program for removing files or directories

so.....
when you were doing "gksu gedit" you were opening a text editor as the superuser.  Executing "gksu gedit rm /etc/fstab.save" tries to open files named "rm" and "/etc/fstab.save" in the text editor.

Thank you Dennis N. 

That removed the files.

Thank you Keith_Helms.

That explained why I could not remove the files. I was only opening the files to edit them. I searched and could not find the exact command. I guess I was not wording it right.

Thanks again for both of your replies.

---

### Post by Bucky Ball on 2015-03-23
Good news. Please mark as solved by following the second link in my signature. ;)

---

