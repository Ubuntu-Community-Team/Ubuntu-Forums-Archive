---
title: "Ubuntu Questions"
date: 2013-03-28
forum: General Help
---

### Post by thatotherdude24 on 2013-03-28
I am just getting in Ubuntu pretty heavy and so far very much so enjoying it. I have a few questions:

1. I am very familiar with Microsoft's Active Directory. Is there anything similar for Ubuntu where I can connect several computers to a server and control policies and user accounts for all of them?

2. Where do I go on a Ubuntu machine to manage policies for that machine? Such as requiring users to enter user names and passwords instead a list of users, password complexity and which groups users are apart of. Pretty much control the local policy of the machine.


Thank you everybody for all the help, I have learned a ton from this forum.

---

### Post by mastablasta on 2013-03-29
> **thatotherdude24 said:**
> I am just getting in Ubuntu pretty heavy and so far very much so enjoying it. I have a few questions:

1. I am very familiar with Microsoft's Active Directory. Is there anything similar for Ubuntu where I can connect several computers to a server and control policies and user accounts for all of them?


LDAP or samba4 or some dedicated server distros have it.

> 
2. Where do I go on a Ubuntu machine to manage policies for that machine? Such as requiring users to enter user names and passwords instead a list of users, password complexity and which groups users are apart of. Pretty much control the local policy of the machine.


i don't know where this is in Unity as i use Kubutnu. but you can do it via command line. have a loot at :
file permisisons: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
man chown: [http://manpages.ubuntu.com/manpages/precise/man1/chown.1.html](http://manpages.ubuntu.com/manpages/precise/man1/chown.1.html)


if you type 
```
man chown
``` 

you will get manual page for chown in terminal
commands you are after are chown, chmod... they are in the first link in the end.

otherwise i htink you can change this with nautiuls (file manager) if you run it as admin.

also have a look here on how to manage users on server: [https://help.ubuntu.com/10.04/serverguide/user-management.html](https://help.ubuntu.com/10.04/serverguide/user-management.html)
also have a look here: [http://ubuntuguide.org/wiki/Ubuntu_Precise_User_Administration](http://ubuntuguide.org/wiki/Ubuntu_Precise_User_Administration)

and if you want a GUI : [http://askubuntu.com/questions/66718/how-to-manage-users-and-groups](http://askubuntu.com/questions/66718/how-to-manage-users-and-groups)

---

