---
title: "Shadow file unknown file type?"
date: 2007-11-02
forum: General Help
---

### Post by abstractcoder on 2007-11-02
I'm new to linux... I was looking in my /etc directory and it shows three files which are listed as "unknown type".  

They are:

1. shadow
2. shadow-
3. sudoers


Are these files suppose to be listed as unknown file types?

---

### Post by Thyme on 2007-11-02
Hi abstractcoder,

If I'm not mistaken, the shadow file contains the passwords of the user info listed in /etc/passwd. The ~ (tilder) at the end of the file means that it is a backup copy. Most files you edit in gedit and other editors will create backup copies with the ~  at the end. The sudoers file contains a list of users that are allowed to run commands as a different user (I think).

Have a look at the following links in your spare time :)

[http://tldp.org/HOWTO/Shadow-Password-HOWTO-1.html]("http://tldp.org/HOWTO/Shadow-Password-HOWTO-1.html")
[http://www.gratisoft.us/sudo/man/sudo.html]("http://www.gratisoft.us/sudo/man/sudo.html")

---

### Post by MrFSL on 2007-11-02
These are important system files and so the ownership and permissions is set to restrict access to users. Because of the restrictions it is displayed as "unknown." In fact they are text files.

---

