---
title: "permissions at mount point"
date: 2008-01-13
forum: General Help
---

### Post by fm1234 on 2008-01-13
I have a partition /dev/sda6 formatted with reiserfs which I want to mount at /media/sda6 in such a way that all the users of the group have write access.

Now, the permissions of the mount point are overtaken by the file system's root folder ownership/permision set. 

How can I change the file system mount point permissions?

Well, when I was writing this post the solution came to me (after one hour wrongly focusing on mount point, mount options, formatting options), so I'll just put it here for someone else:

1) mount the file system, e.g., sudo mount /dev/sda6
2) cd to the mount point, e.g., cd /media/sda6 (yes, mount point is named the same as device)
3) change permissions of the the current folder i.e., the dot ".", e.g. sudo chmod 770 .
4) optionally change ownership, e.g. sudo chown user:users .

---

### Post by mccorkle on 2008-01-14
You could also set the mount point up in /etc/fstab to allow user mounting via the "user" option in the 4th column.  The chown/chmod the target mount point so that the user in question could mount to that point.  

::Mark McCorkle

---

### Post by fm1234 on 2008-01-14
Yeah, I looked into that but it's not applicable in my case since in my computer the whole family logs on while the computer stays on. 

To use that option, I would need the mount to happen per user at log-on time (instead of boot time). I'm not even sure where I would do that, and I would have to do it for each user.

Also, it is not as practical when a user is logged in and I need to use a terminal and su to my own login.

Anyway, thanks for the reply.

---

