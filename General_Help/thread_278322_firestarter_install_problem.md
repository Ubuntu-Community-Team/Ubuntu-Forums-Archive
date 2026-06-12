---
title: "firestarter install problem"
date: 2006-10-16
forum: General Help
---

### Post by andb on 2006-10-16
when installing firestarter via sudo aptitude install firestarter, I have the following error:

Selecting previously deselected package firestarter.
(Reading database ... 99944 files and directories currently installed.)
Unpacking firestarter (from .../firestarter_1.0.3-1.1ubuntu4_i386.deb) ...
Setting up firestarter (1.0.3-1.1ubuntu4) ...
Failed to load file "/var/lib/gconf/defaults/%gconf-tree-tr.xml": Error on line 751 char 59: '.' is not a valid character following a '<' character; it may not begin an element name

Firestarter does not install properly, the startup wizard runs, the program will not open,  /etc/init.d/firestarter does nothing, whether I try start or status. 

Any ideas?

---

### Post by wieman01 on 2006-10-16
Dumb question (but perhaps the most obvious one)... Can you post the contents of this little troublemaker please?
> /var/lib/gconf/defaults/%gconf-tree-tr.xml
There is an issue with special characters...

---

### Post by andb on 2006-10-16
Thanks for the reply. After serious frustration, I just used less to look through a few of these xml files, and would you believe it, tried firestarter again and it installed fine. Thanks again, guess I wont know what was really the cuplrit...

---

