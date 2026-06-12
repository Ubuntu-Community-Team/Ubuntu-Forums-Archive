---
title: "Launch a command like a user in root terminal"
date: 2007-07-27
forum: General Help
---

### Post by romaluca on 2007-07-27
I'm in root terminal.
I must launch a command like an user 

i try with sudo -u username command

but the home used is /root/ and not /home/username/

I want use /home/username 

How can i do?
Thanks

---

### Post by Koybe on 2007-07-27
Simply change the user :
```
su - username
```
Then```
exit
``` when you're done.

---

### Post by designwiz on 2007-07-27
if you donot have any account than root then creating a new user then login, and ur pwd would be /home/<username>

To create a new user account Go to System>Administration>User and Groups

If no GUI is present and ur logged in as root, try using startx and following the above steps!

---

