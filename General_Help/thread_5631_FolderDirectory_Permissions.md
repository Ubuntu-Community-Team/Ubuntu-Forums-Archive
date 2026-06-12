---
title: "Folder/Directory Permissions"
date: 2004-11-20
forum: General Help
---

### Post by dubdubdub on 2004-11-20
Is there an easy way (terminal perhaps) to change all the permissions of an entire directories contents?

I copied some files off of a CD to try in Wine (photoshop, megaman!) and now they are in my trash can, with only "read" and "execute" permissions checked. It is a huge pain in the ass opening subdirectories, select all, get info, change permissions etc. etc.

Or a command to empty my user trash as root?

---

### Post by jomohke on 2004-11-20
The trash is simply the .Trash folder in a users home directory, which you can access with the terminal.

You can use chmod with -R (stands for recursive) - which means it will go inside subdirectorys. You can also use the * wildcard character which will represent any characters. So:

chmod 777 -R .Trash/*

will change the permissions of every file in trash, including subdirectories to 777. (assuming you are in the users home directory)

Similarly
chmod 777 .Trash/b*r

will change the permissions of every file in trash that begins with b and ends in r, but it wont go inside subdirectorys.

The same options will work to delete files. So to empty the trash as root use

rm -R /home/youruser/.Trash/*

---

### Post by dubdubdub on 2004-11-20
That worked! Thanks for you help.

---

