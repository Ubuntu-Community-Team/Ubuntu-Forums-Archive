---
title: "read-only need to make it read and write"
date: 2017-05-19
forum: General Help
---

### Post by gordon33 on 2017-05-19
Hello ll

I am using Ubuntu 16.10 and one of my excel files is telling me it is read only.  What do I need to do to make it read and write?

I tried right clinking on the file and from the pull down menu selected "Properties".  Under the permission tab i checked the 3 boxes for read and write.  Still the file is read only.

Gordon33

---

### Post by ajgreeny on 2017-05-19
Who created the file, where did it come from, is it local in your home, and who is the owner of it?

The right click ->Properties will show the owner; if it is not you it will not be possible to change permissions until you either change its owner to you, or change its permissions as root.

---

### Post by gsahli on 2017-05-19
start with:
Use the Terminal. Read the manual for the chown command:
man chown

---

### Post by gordon33 on 2017-05-19
Hello ajgreeny and gsahli

Thank you for the replies.

I got it to _read and write_ by changing the file extension from xlsx  to xls.

ajgreeny; how would I change its owner or change its permissions as root.

I am the owner and the file is on my computer.  When I right click pick properties and then go to the permissions tab "Me" is listed as the owner.  While I am not the originator of this xlsx file I have been the only user for the last 5 years.  It is the second computer I have moved the xlsx file to and also saved it on a flash stick.

gsahli:  I will learn about the chown command. 

Thank you again gsahli and ajgreeny for your help

gordon33

---

### Post by ajgreeny on 2017-05-19
You should change permissions using the **chmod** command and change owner with the **chown** command.
To make changes to files not owned by you you will need to use **sudo** as prefix to the commands to raise your user to root temporarily.
See Root-Sudo in my signature for the use of **sudo** to get root permissions.

See [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
or use **man chown** and **man chmod** in terminal to read the manuals.

---

### Post by gordon33 on 2017-05-20
Hello ajgreeny

I got the file to go to read and write. using the chown command.  Thank you for your instructions,


Gordon33

---

