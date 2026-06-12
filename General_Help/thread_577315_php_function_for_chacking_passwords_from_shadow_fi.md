---
title: "php function for chacking passwords from shadow file"
date: 2007-10-16
forum: General Help
---

### Post by tofighi on 2007-10-16
I want a php class for authenticate a user from a web interface from his username and password of him/her.
for example I have a user name of **temp** with this shadow information:

**temp:$1$N8KVrFji$0lW5iBIRw7z2pm1NiK1R9/:13802:0:99999:7:::**

is there any php class for this purpose to get username and password and check whit this information?

**Thanks in advance**

---

### Post by indytim on 2007-10-16
I always use a MySQL table to at least record my users id and encrypted password (I use md5 with all upper's).  When a user enters their id and password, I authenticate via a read from the MySQL table.  If it's a match, I set a session variable to identify the user priv's within the system.

If you track on over to HotScripts, you'll probably find a ready-made script to do what I described above.

IndyTim

---

### Post by tofighi on 2007-10-16
I don't like this method, because if user change his/him password via ssh (passwd command) you can't insert his new password to your table, I want a php function or class to authenticates as like as linux dose.
Any Suggestions?

---

