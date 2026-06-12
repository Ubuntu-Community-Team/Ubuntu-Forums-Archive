---
title: "How to prevent sudo from changing PATH?"
date: 2007-02-22
forum: General Help
---

### Post by dabd on 2007-02-22
How can I prevent sudo from resetting my PATH?  I would like to keep my user PATH when executing sudo.
Searching the forum for answers and googling just confused me more.
I tried adding the following line to sudoers, but it doestn't work:
Defaults env_keep = "PATH"

Any help would be appreciated.

Thanks.

---

### Post by DagMan on 2007-02-24
Sorry if this is not the answer you're looking for at all, but I'm not familiar with how to add to the PATH variable in the sudoers file.
The global PATH is in the file /etc/environment if that is any help.

---

### Post by majoridiot on 2007-02-24
System-->Administration-->Users and Groups

select root, then "Properties" and the advanced tab...

first entry is home directory- change /root to /home/<whateveryouwant>

---

