---
title: "why such unrestrictive home directory permissions?"
date: 2007-11-17
forum: General Help
---

### Post by Zelut on 2007-11-17
I was just noticing that in gutsy home directory permissions are readable and accessable by the general public.  What is the reason for this?  i would think that user home directories should be readable and accessable only by that user.

Any thoughts?

---

### Post by mike555 on 2007-11-17
Your documents etc . should not be able to open from a different user or the general public , unless you gave them root privileges .........   unless you mean different users that set down and use your computer using your user account ..... Ubuntu is good , but not good enough to see hows using your computer .......

---

### Post by Zelut on 2007-11-18
no, I mean on a multi user system the privs on /home directories look like 755.  I think more responsible, private system the directories in /home should be 770 so that other people with accounts on the system should not be able to see anything within another users home directory.

---

### Post by ivan.tg on 2008-02-19
Hi, i was searching for answer to the same question but to little avail so far. Anything new?

---

### Post by pointone on 2008-02-19
```
man umask
```

Default umask in Ubuntu is 022 (results in directories created with 755, files with 644).

Simply change/add "umask 007" in your .bashrc file or /etc/profile (for system-wide changes) and all new dirs/files you create will be 770/660. To change existing files, "chmod 770 -R /home/username".

---

### Post by Ptero-4 on 2008-02-19
Thanks, pointone. I was looking for that as well.

---

