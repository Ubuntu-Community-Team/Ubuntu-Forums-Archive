---
title: "How do groups really access files?"
date: 2007-05-27
forum: General Help
---

### Post by doccpu on 2007-05-27
If fred is in login group fred and of group users why cant he make a dir or file in a dir that has user as a group priviledge? How do groups really acess files?
I am getting real angry at the problems of a user not being able to acces or create a file or dir. If he owns it he can, if he is in a dir of a group he is in he cant . What IS the precedence of what  groups can use or create a file or dir? 


I made a dir. owned by root and group of mine. worked fine. 
I changed a higher dir to be owned by root and group i am a part of. I cant create anything in the higher dir or now in the dir that is supposed to be mine. What the hell is with that?

---

### Post by ellisdee on 2007-05-28
Possibly the group doesn't have write permissions allowing you to create files, etc

Best to look at chmod, here's a tutorial - [http://catcode.com/teachmod/chmod_cmd.html]("http://catcode.com/teachmod/chmod_cmd.html")

---

### Post by pmg on 2007-05-28
The group listed for a user in /etc/passwd is their "primary" group.  When they create a file, that is the group that will own it.  Other groups they are listed as members of in /etc/group are "extended" groups.  They will be able to read/write/execute files owned by those groups as per the group file permissions (set by chmod.  See above post.)  To help see this, run the **id** command to get userid and group info for the current process. You'll see your userid (uid) followed by your "primary" group id (gid), and then the list of "extended" groups you're in.  Also look at the help for the **newgrp** command, to see how to set a different gid (i.e. primary group.)

---

