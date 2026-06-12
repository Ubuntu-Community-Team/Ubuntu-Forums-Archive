---
title: "remove gedit recently used list"
date: 2008-03-23
forum: General Help
---

### Post by beau_cg on 2008-03-23
Hi all,

I know I can delete the recently used file in my home directory, which remove the list
when I run gedit.
But, when I run gksu gedit, the recently used list appears with all the files I edit with gksu gedit.
How can I remove that?

Thanks in advance

---

### Post by smoker on 2008-03-23
just a suggestion, wouldn't you have to remove recently used files as 'root' to remove them running gedit with gksu?

---

### Post by x1a4 on 2008-03-23
Hi,

su is short for switch user.  When you run something with sudo or gksu[do] you execute application as that user, as if you had logged in as that user and opened software normally.  By default sudo and gksudo switch to root, unless you use the **-u *<user>*** option.  This means that any configuration file(s) (including list of last opened documents) will be in that user's home directory.  

If you run gksudo without the -u option remove the necessary files from root's home directory /root/ otherwise from that user's home directory.  You can do this by running your file manager using gksudo, logging in as the user in question, or from the command line, either by using sudo or su.

---

### Post by beau_cg on 2008-03-25
thanks!!:)

---

