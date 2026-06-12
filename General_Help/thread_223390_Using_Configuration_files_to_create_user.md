---
title: "Using Configuration files to create user"
date: 2006-07-26
forum: General Help
---

### Post by mathon on 2006-07-26
Hi,

I want to create a new user by hand with the help of the corresponding configuration files. In the course of that I used the following steps:

1) Create new user under /etc/passwd: sudo vipw
user:x:1003:1003:test user:/home/user:/bin/bash (I used the next free number for UID and the same number for GUID)

2)Under etc/shadow: user::13355:0:-1:-1:-1:-1:0

3)Under /etc/group: user:x:1003:

4)Under /home: sudo mkdir user

5)Configure owner and group: chown user:user ./user

6)chmod o-rwx user (No rights for the others, read and execute rights for the users which are in the same group as "user")

7)set password sudo passwd user 
---------------------------------------------------------------------------

*) Is that correct and useful?

*) Has to be the new user in any other groups in order that this new user can work effectively? (e.g. in admin group or in any other group)

*) How can I find all files which are owned by this user? - because when I want to delete this new user I want to delete his files.

*) Should the search after the files which are owned by this user be executed before I delete the entry in the /etc/passwd or after that?

Kind Regards

---

