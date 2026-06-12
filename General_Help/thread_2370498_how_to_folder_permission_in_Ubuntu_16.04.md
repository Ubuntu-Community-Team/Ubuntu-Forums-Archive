---
title: "how to folder permission in Ubuntu 16.04"
date: 2017-09-04
forum: General Help
---

### Post by ravinippu on 2017-09-04
I am new in Linux
Let's say we have 4 user:
u1, u2, u3, u4
And we have 2 directory or folder:
d1 and d2
Now how to give user u1 u2 u3 u4  rwx  permission to folder d1 
and folder d2 have user u1 rwx permission user u2 and u3 have read only permission and u4 don't have access to folder d2

---

### Post by TheFu on 2017-09-04
Use 2 groups.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Put the RW users into a group.

d1 owned by u1 or u2 or u3 or u4
chgrp d1-guys d1
chmod g+rwx d1

d2 owned by u1
chgrp d2-guys d2
chmod g+rwx d2
chmod o-a d2  # u4 isn't in the d2-guys group

If you want to force all files and directories below d1, d2 to be set with the correct groupid, the do a chmod g+s on both directories too.  Whoever is the own of each directory is the only person who can manage permissions.

Or if you want to make this harder to follow, use ACLs, but ACLs can be disabled, ignored, with a mount option.  Of course, root/sudo can do anything, so if any of these users have that capability, then they can gain access at any point.

---

### Post by ravinippu on 2017-09-04
> **TheFu said:**
> Use 2 groups.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Put the RW users into a group.

d1 owned by u1 or u2 or u3 or u4
chgrp d1-guys d1
chmod g+rwx d1

d2 owned by u1
chgrp d2-guys d2
chmod g+rwx d2
chmod o-a d2  # u4 isn't in the d2-guys group

If you want to force all files and directories below d1, d2 to be set with the correct groupid, the do a chmod g+s on both directories too.  Whoever is the own of each directory is the only person who can manage permissions.

Or if you want to make this harder to follow, use ACLs, but ACLs can be disabled, ignored, with a mount option.  Of course, root/sudo can do anything, so if any of these users have that capability, then they can gain access at any point.
Things are not clear because if i put u1, u2, u3, u4 in a "readwrite" group and u2, u3 in "read" group then

chgrp d1-u1u2u3u4 d1
chmod readwrite+rwx d1

but folder d2 have only u1 have permission to rwx and u2, u3 have read access and u4 have no access to d2 then

chgrp d2-u2u3u4 d2
chmod read+r d2
chmod o-a d2  # u4

d1 and d2 folder created by sudo user on ubuntu 16.04
here the thing mess up, that's why Linux is for genius, but I am not so I want exact commands

---

### Post by TheFu on 2017-09-04
It just takes practice, that's all.  Don't forget about the "other" and "owner" permissions.

Start with something easier.  Show your exact work with exact commands.
Do you have d1 working as needed? Y/N?

---

### Post by ravinippu on 2017-09-05
> **TheFu said:**
> It just takes practice, that's all.  Don't forget about the "other" and "owner" permissions.

Start with something easier.  Show your exact work with exact commands.
Do you have d1 working as needed? Y/N?
d1 have 777 permission so yes it working fine

---

### Post by TheFu on 2017-09-05
777 is for lazy people who don't care about security. ** It is dangerous to the entire system**, as it provides a beach-head for bad-guys to use for placing stuff outside /tmp/ where we expect to see them.  Whenever I see a how-to that suggests using 777 permissions, I know they are either lazy or don't have a clue.

How hard is it to put the users into a group, make the directory owned by that group and do a chmod 770?  30 seconds of effort?

Might I suggest that you always post the output from **ls -al** when asking about permissions.  We need it for the file and the directory where the file is stored usually to be of any help.

---

### Post by ravinippu on 2017-09-09
I have no clue. Ok, how to see... let's say /home/xyz/share
I gave several user rwx permission on "share" folder and several user have r-x permission.
And I forgot everything which user have what permission and how many user have permission on "share" folder. Now how to see how many user have permission on this folder and what are the permissions

---

### Post by TheFu on 2017-09-09
If you are so new that you cannot run **ls -al** on a directory and post it, perhaps I cannot help at all.
I am sorry.

Here [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a free book that you can either purchase or just download the PDF to read.  Chapter 3 is all about the 'ls' command.  It is one of the most basic tools on any Unix-like system.

Unix permissions are organized into 1 owner, 1 group, and "others".  Any userid who isn't the owner or in the group, is "other"  It does not mean "everybody" as some books explain.  It means everyone ELSE EXCEPT the owner and group members.  This subtle different seldom matters, but based on your question, it could for you.

That book has at least 1 chapter on permissions (chp 9) too, but without the background leading up to that, it won't be helpful.

Good luck.  And please stop using 777 permissions. You will thank me when your system isn't totally hacked.

---

