---
title: "[SOLVED] Modifying .conf file of program"
date: 2008-03-09
forum: General Help
---

### Post by mike g on 2008-03-09
I am attempting to modify/change a .conf file but am unable to make the change.

I am using Xbuntu on an old HP Pavilion and am trying to modify a file called gpsk31.conf.

I have attempted to change it using the "vi" command but it did not work.  I have attempted to open an new directory to make the modifications but cant seem to make the new directory take.  I even tried copying the old .conf file into a new file using the "cp" command, again no luck.

Can anyone give me a step by step course in modifying and saving a .conf file?

Help, 

Mike

---

### Post by banewman on 2008-03-09
Mike, the first thing when you're having trouble changing a file is to check to see who owns it.
If you right click a file and select properties, then the permissions tab, you'll find out who owns the file,
If it is not you then you can make changes to the file stick using the sudo command.
e.g. sudo gedit /path/to/gpsk31.conf (the path might be something like /usr/bin/gpsk31.conf - as an example)
The "vi" command is to open a text editor that is terminal based.
The gedit I used is for the normal text editor in ubuntu.
But the important point is to edit a file you don't own is to use admin rights with the sudo command and your login password.
:)

---

### Post by mike g on 2008-03-10
Thank you this solved this problem but another one has raised its ugly head completely unrelated to this problem......I really appreciate the help, a lesson learned.

---

