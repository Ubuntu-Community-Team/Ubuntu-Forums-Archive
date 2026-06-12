---
title: "Using Chmod And ACLS"
date: 2017-10-16
forum: General Help
---

### Post by darkmatter176 on 2017-10-16
[COLOR=#111111][FONT=Ubuntu]If i have 3 Users, all apart of the LOCAL group - User1,User2,User3[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]And inside User1 Home directory /scripts , there is a script[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I need User2 to have write perms to this script (Just Write Perms)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]i also need User3 to have Execute perms, and to run the script(Just Execute Perms)[/FONT][/COLOR]

---

### Post by TheFu on 2017-10-17
Welcome to the forums.

Make anyone who needs to write either the owner or in the group.  Make anyone who needs only r-x to be "other" - not in the same group for the file.  That means using the "LOCAL" group cannot be done for this file in the place with the current owner.

No need to use ACLs.

Scripts can't just have execute and work. They must also have read.  Programs (compiled) **can** have just execute permissions and will work just fine.  rwxrwxr-x is probably what you need here.  user1/user2 need to be in their own group.  If user1 doesn't need to be involved (it isn't in the requirements above), then have user2 copy the file over (probably into ~/bin/) and then you can use rwxr-x--- permissions.

BTW, Unix userids and groups really need to be all lower-case.  Also, I much prefer ~/bin over ~/Scripts for a place to store my custom scripts.  That is much more common on Unix systems.

There are some interesting different permissions with 711 (rwx--x--x) which make perfect sense, just not for scripts (interpreted files).

---

### Post by HermanAB on 2017-10-17
As pointed out above, to execute, you also need to read it.  Also, if someone has write access, then he can just as well also have read access.  

So normally one would use of the following: read, read-write, read-execute, read-write-execute

Other combinations don't make much sense.

---

