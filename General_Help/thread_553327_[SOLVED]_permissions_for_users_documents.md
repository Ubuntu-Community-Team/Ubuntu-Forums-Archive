---
title: "[SOLVED] permissions for users documents"
date: 2007-09-17
forum: General Help
---

### Post by brummie on 2007-09-17
i need to stop other users viewing each others documents on a machine.
I have tried changing permissions of their user folder but that causes login problems for gnome.

Any idea what i can do??

---

### Post by raijinsetsu on 2007-09-17
First, we need more info.
What groups are the users in?
What groups do the files belong to?
What directories are these files in?

Most likely, it's as easy as "cd /home; sudo chmod -R o-rwx *"

---

### Post by brummie on 2007-09-18
> **raijinsetsu said:**
> First, we need more info.
What groups are the users in?"

they all are in /home

> **raijinsetsu said:**
> What groups do the files belong to?"

they belong to their own username groups

> **raijinsetsu said:**
> What directories are these files in?"

/home/username

Every user can see each others documents.
When i try from the GUI all i get is gnome moaning about setting the permissions back :(

i'll wait for a reply before i run the command

TIA

---

### Post by raijinsetsu on 2007-09-18
Ok... Most likely, everyone has read access.
Do this:
```

cd /home
sudo chmod -R o-rwx *

```
This will remove read, write, and execute permissions for everyone except those in the users group or the users themselves.

---

### Post by brummie on 2007-09-19
That worked perfectly thankyou. :)

---

### Post by raijinsetsu on 2007-09-19
You might want to follow up with making sure the hidden directories have those permissions too.
```

cd /home/UserA
sudo chmod -R o-rwx .*

```

unfortunately, this doesn't work recursively very well...
There is a way to do this with the "find" program, but seeing as I'm not at a linux computer right now, I can't give you a working example :)
You can probably use the thread tools to mark this thread as solved. :)

---

### Post by nvteighen on 2007-09-19
But, you surely don't want that happen again, so, go to each users' home folder, locate the file .bashrc and, at the end, add this line:

```

umask 007

```

No, it's not to unmask James Bond ;) What that does is to automatically remove all permissions for "others" for any new file the user creates. If you want to remove all permission except the "user's", use:

```

umask 077

```

I've heard there's a way to do this system-wide and so you don't need to enter each user's home, but not to sure if it's appropriate.

---

