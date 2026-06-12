---
title: "Directory permission question"
date: 2008-01-19
forum: General Help
---

### Post by johan.alfa on 2008-01-19
Hello,

Is the following possible.
( as root or admin ) I would to create some directories in a normal user home directory.

The  user should be able to create files, subfolders etc. just as other folders but...
He should not be able to remove or delete it.

I tried something like this.
mkdir -m 1777 /home/user/stickydir

My findings are.

It works in every other place but not in the home dir of a user.
When I try it in the home dir of a user he is always able to delete the directory.

greetings,

---

### Post by rune0077 on 2008-01-19
I think (but aren't sure) that users always has full permission to files in their own homefolder. What you could do, I suppose, is to place the folder somewhere else, and then make a link to it inside the users homefolder.

---

### Post by johan.alfa on 2008-01-19
Hello,

I tried already the linking  but the user can delete the link so.
I really need something to protect a user from deleting those folders.

greetings,

---

### Post by johan.alfa on 2008-01-20
Anybody has an idea?

---

