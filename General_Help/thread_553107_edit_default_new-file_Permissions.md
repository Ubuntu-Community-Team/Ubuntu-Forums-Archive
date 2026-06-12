---
title: "edit default new-file Permissions?"
date: 2007-09-17
forum: General Help
---

### Post by bsmith1051 on 2007-09-17
I have a shared folder on my Ubuntu 7.04 system where my wife and I both save/edit files.  We have separate logins and use Fast User Switching.  We are both a member of the other person's Group.  The problem is that files we create all default to the Group having just read-only permissions.  

How can I make our new files default to Group read-write?

P.S.  Yes, I've tried searching these forums for "default permissions" but haven't found a straight-forward answer.

---

### Post by jamvegan on 2007-09-17
I do not know of anyway to change the default on a per-directory basis, but if it's okay for all files that you and your wife create anywhere to have group write permission turned on, then you can each add:
```
umask 002
```
to your ~/.bashrc files, and that should do it.

---

### Post by bsmith1051 on 2007-09-17
where in the file, or does it matter?  Can I just append it to the very end?  And will this affect all programs, i.e., not merely command-line activities?

P.S.  Thanks for your help!

---

### Post by pmg on 2007-09-17
You could create a ~/.bash_login file and put the **umask 022** in there, or put it in your ~/.bash_profile.

Another option, if you want all files created under the directory *foo* to have the group owner *bar* you could:
[B]sudo chgrp foo bar
sudo chmod g+rwxs foo[/B]

Turning on the group **s** bit of a directory makes all files created in it take on the group owner of the directory.

---

### Post by jamvegan on 2007-09-17
> And will this affect all programs, i.e., not merely command-line activities?
Excellent question!  I'm glad you asked.  I pretty much only create files in the terminal in Linux, so I didn't even think about this.  If you put it in ~/.bashrc it would only affect what you do in bash.  For what you want, you should add:
```
umask 002
```
to the end of ~/.profile.

---

