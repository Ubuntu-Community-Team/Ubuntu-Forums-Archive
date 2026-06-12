---
title: "Samab Question"
date: 2007-10-25
forum: General Help
---

### Post by ghandi69_ on 2007-10-25
Hey guys,

Tonight I spent some time setting up a server, it was a straight install of gutsy server edition, and all I installed on it was samba and a ftp program.

Anyway, Samba seems to be running fine on my network, I can copy files to the server and back just using nautilus.  However, it seems certain files will not copy.  I wanted to copy my .fluxbox file, for example, which contains files like init, keys, menu, startup, among others.  It will copy the .fluxbox folder, but none of the files inside will make it over.   Everything else seems to copy fine, except this issue.

Any ideas?

-- properties of these files claim they are --> application/octet-stream

---

### Post by benerivo on 2007-10-25
Might be a permissions problem, but if you have taken other files from the same location then it probably won't be. Check the permissions of the stuff that won't transfer. I remember the first time i tried samba, i copied some files to my macmini with no error messages and later found i just had several empty folders. Changing the permissions on ubuntu so other users had full access solved it.

---

