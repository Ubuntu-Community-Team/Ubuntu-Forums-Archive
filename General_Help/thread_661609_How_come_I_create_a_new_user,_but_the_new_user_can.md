---
title: "How come I create a new user, but the new user can view the contents of my /home dir?"
date: 2008-01-08
forum: General Help
---

### Post by enthusaroo on 2008-01-08
Hey everyone,

I have a person coming to stay with me for a few weeks. I would like to give them access to my computer. I run Ubuntu 7.10. But I do not want them to access my personal files.

I am the first and only user for this Ubuntu installation. So I created a new user. But when I log in as that use, I find that I can still access my private files. :( I've gone through all the options under "Users and Groups". What do I need to do in order to restrict other users from viewing my files? :confused::confused:

Please help with this simple (but important) problem!

---

### Post by Sef on 2008-01-08
You could encrypt them.  Check synaptic for encryption software.

---

### Post by jeffus_il on 2008-01-08
The new user is a member of a group, if it is the same group as yours, you can remove group read access from all your files quickly by using the chmod -R command in your home directory.

do an "ls -l" in your home directory.
See what the permissions are on the files.
they are divided into three groups, user, group, and other.
If you need more help , post.

---

### Post by gwbennett on 2008-01-08
User friendly method:
Places, home folder
Navigate "up" one level.
Right click home folder and go to properties
Permissions tab, change "others" folder access to none, and file access to none.
hit "apply permissions to enclosed files"
Close.

Done.

I did this successfully after finding that my "guest" account could access my folders. Worked beautifully.

---

