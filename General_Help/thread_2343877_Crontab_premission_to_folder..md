---
title: "Crontab premission to folder."
date: 2016-11-20
forum: General Help
---

### Post by krichukz on 2016-11-20
How can i make crontab to do:

Every work day each hour:
folder /home/Public
Gives RWX premissions to root 
Gives RW premissions to group and others.


do i need to make script first?
and what is the right syntax for this?
Thanks in advance.

---

### Post by ian-weisser on 2016-11-20
Root should already have permission to do anything it wishes in your /home dir.

Multi-user service applications (like folder sharing) should _not_ be run under your user. They should be run by a special-purpose user that doesn't have shell access. This is usually called a 'system user'
You should not be granting permisson to anybody to go wandering around in your /home folder. Public folders usually belong in /var/ , and owned by the same system user - not you, not root.
These are basic security precautions. Else you may well get compromised, and all your data lost...or released.

If you are trying to share Media files, use a proper Media Server application.
If you are sharing collaborative documents, use a specialized application (like etherpad) for the purpose.
If you are creating a repository of files, use a proper File Server application.

---

### Post by krichukz on 2016-11-20
Well i wrote it a bit wrong .
[COLOR=#000000]Every work day each hour:[/COLOR]
[COLOR=#000000]folder /var/Public[/COLOR]
[COLOR=#000000]Gives RWX premissions to folder owner[/COLOR]
[COLOR=#000000]Gives RW premissions to group and others.

Its just i need to create a folder that is for all users, and to give premission RWX to owner and RW to other users and group each hour.
I'm kinda new to all ubuntu stuff to bare with me :)

Its an assigment in school.[/COLOR]

---

### Post by howefield on 2016-11-20
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.

Thread closed.

---

