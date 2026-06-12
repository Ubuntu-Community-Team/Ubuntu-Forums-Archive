---
title: "Confused - group &amp; user permissions"
date: 2005-05-28
forum: General Help
---

### Post by Krank on 2005-05-28
OK, now then:

I have a dir, let's call it /var/downloads/ . I want to give complete rwx access to this directory to a set number of users.

Should be easy, right?

The theory:

1. Create a new group called "remoteusers" (because the users who are going to have acess to the dir are... well, they're remote users. Samba FTP, whatever. Not the point.). [done via the graphical interface]

2. Add the users to the group. [done via the graphical interface]

3. Set group of dir to "remoteusers". [done via "chgrp -R remoteusers /var/downloads/"]

4. Set g=rwx on the dir. [done via chmod -R g=rwx /var/downloads]

...only it doesn't work. I see that the correct group owns the dir, and that the rwx is in place (dir -l). But still, the user "krank" (me, added to the group) cannot create new files or edit old ones in said directory.

What gives?

---

### Post by Krank on 2005-05-28
Nevermind, it suddenly worked. Weird.

---

### Post by JonahRowley on 2005-05-28
You have to log out (to my knowledge) and back in to be in the new group.  Use the **groups** command to see which groups you belong to, if it's not in there, log out then back in.  If it's still not in there, or it is in there and you still can't write to the dir, something else is wrong, but I think this is your problem.

Also, if you want this to be a common directory and want people to be able to change eachother's files, set the **sgid** bit on the directory.  This will make all files created in this directory (not moved to, since that doesn't create a new inode, only changes a directory entry) to have group ownership of the directory, not the user's native group.  The command for that would be **chmod g+s /var/downloads**.

---

### Post by JonahRowley on 2005-05-28
[QUOTE=Krank]Nevermind, it suddenly worked. Weird.[/QUOTE]

I bet you logged out before it would work ;)

---

### Post by placidoaps on 2006-10-13
Hi,

I have the same problem, and I only solved it by rebooting (didn't try logoff/login)

The question is... why?!?

Does anyone know???
](*,)

---

### Post by uros678 on 2006-10-13
My guess would be that when a user logs into the system the system reads the uid and gid numbers a user belongs to. When you change those settings the system doesn't automaticaly read the new setting, but one has to log out and log back in for the system to read the new settings.

Probably that's not the right explanation, but it's how I picture it.. :D

Best regards,
Uros

---

### Post by bcollignon on 2006-10-14
Isn't there a HOWTO or tutorial concerning groups?

---

### Post by JonahRowley on 2006-10-14
> **bcollignon said:**
> Isn't there a HOWTO or tutorial concerning groups?

If you ask me, this isn't HOWTO territory.  HOWTOs and tutorials are not the answer to everything, however, they're better covered in resources such as the [Rute Book](http://rute.2038bug.com/index.html.gz) or any other such text ([like Marcel Gagne's](http://www.amazon.com/Linux-System-Administration-Users-Guide/dp/0201719347/sr=8-4/qid=1160856927/ref=pd_bbs_sr_4/002-0580015-5585616?ie=UTF8) book on the subject).

---

