---
title: "Loss of administration Authorization"
date: 2008-05-29
forum: General Help
---

### Post by Euphorion on 2008-05-29
Hallo

I am fully new to Linux and Ubuntu. I have managed to install Ubuntu on my Fujitsu Mi-2550 Laptop, it works very well.

During installation I created an Account having Username=Myname and Password=MyPW. With this User I could administer the machine (add/delete software etc). I then decided to create a reserve administrator user and a restricted user for surfing the Internet. I did this using Systen->Administration->Users and Groups. All went well and whilst logged on with Myname I could administer the machine. I decided to try my new Admin-User using User Switch (top right in the launcher panel, the screen flashed random colors and the PC hang up. I switched off and restarted and logged in with Myname, but I had then lost all administration rights and could not correct my doings. I reinstalled Ubuntu and repeated the procedure for creating the two addition users. I then used logoff (red button top right) to change the user, the desktop disappeared a lot of lines flashed over the screen and the desktop reappeared with a logon screen, logged on with new admin user and once again I could not administer the system. When I tried to unlock Users and Groups nothing happened for approx 30 secs and then a popup appeared "Unexpected error has occured" So I reinstalled Ubuntu for the 3rd time.

What am I doing wrong? 

Thanks in advance

---

### Post by mali2297 on 2008-05-29
Have you set the new user's name to **admin**, by any chance?

---

### Post by Euphorion on 2008-05-29
Thanks for your reply

The first time around yes.

I created a user with Username=admin and a user with Username=restricted.

The second time around i created the following two user names

Username=peteasadmin and Username=restricted.

In both cases I lost the administration rights. At the moment I am running Ubuntu with the Username created during installation and am keeping well clear of "Users and Groups" but am confused as to why this should happen. By the way which file(s) contain the user info and can one copy these to a stick for safety.

---

### Post by mali2297 on 2008-05-29
There is already a group called *admin* which all users with administrative privileges belong to. If you name a user by that name then the system might get confused and break.

Perhaps you should try using the command line instead of the graphical *Users and Groups*. To add a user *angela* with administrative privileges, type
```

sudo adduser angela
sudo adduser angela admin

```

> 
By the way which file(s) contain the user info and can one copy these to a stick for safety.

The user info is in /etc/passwd whereas the group info is in /etc/group.

---

### Post by Euphorion on 2008-05-29
Thank you very much.

In future I will use the command line method as suggested. I will have to read up on add user, as a password has to be assigned and adduser will have an appropriate switch.

Kind Regards

---

