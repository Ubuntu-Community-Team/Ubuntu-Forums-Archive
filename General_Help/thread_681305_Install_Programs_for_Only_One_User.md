---
title: "Install Programs for Only One User"
date: 2008-01-28
forum: General Help
---

### Post by mlissner on 2008-01-28
I've been looking around, and I'm beat. How can I install a program such that only certain users on the system can access it? 

For example, I like to install cracking software such as john, but doing so means that such programs are available to all who use this computer. Thus, anybody who can figure out that john is installed can sit around cracking /etc/passwd.

Any thoughts on this in the community?

---

### Post by Shootfast on 2008-01-28
chown the binary executable?

eg type "which john"

then "sudo chown user:user /path/to/john"

---

### Post by mlissner on 2008-01-28
Ah ha. I had a feeling this was the trick. You were close. I also had to do:

chmod 700 /usr/sbin/john

otherwise all was for not.

---

