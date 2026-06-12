---
title: "mount"
date: 2008-01-08
forum: General Help
---

### Post by irshan on 2008-01-08
1 there are 3 partions in media directory like sda1,sda2 and sda3 now i want to mount in to desktop how can do in terminal

2.how to create new user account in ubuntu

3.if i forget useraccount or password is there any way to find

---

### Post by erfahren on 2008-01-08
> **irshan said:**
> 1 there are 3 partions in media directory like sda1,sda2 and sda3 now i want to mount in to desktop how can do in terminal
You'd probably want to unmount them from /media and then remount them - you could name them what you want. I think they would show up on the Ubuntu desktop by default unless you go into the configuration editor (gconf-editor) and check them to not show up (apps > nautilus > desktop) -  I could be wrong on that.

There are lots of guides on mounting, see for instance:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

> 2.how to create new user account in ubuntu
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

> 3.if i forget useraccount or password is there any way to find
I'm not sure, but you could change the account's password as superuser - the users will show up under the "users" in the "Users and Groups" 

some other info you may find useful here: [https://help.ubuntu.com/community/SystemAdministration](https://help.ubuntu.com/community/SystemAdministration)

---

### Post by erfahren on 2008-01-08
I was looking through my bookmarks for something else and came accross this:
[How to reset your password in Ubuntu](http://www.psychocats.net/ubuntu/resetpassword)

---

