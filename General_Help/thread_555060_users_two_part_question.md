---
title: "users two part question"
date: 2007-09-19
forum: General Help
---

### Post by stumped on 2007-09-19
I am running ubuntu edgy eft and gnome.  Is there a way to set up a second user account that will automatically log in without a user name and password, yet, still require a name and password to log in to my account?  
If there is, can it be set up so my account will have full control over the other account, yet, the other account can not touch mine?
I am new to linux so please, if these things can be done, tell me in "dummy terms", so I can understand.

---

### Post by lisati on 2007-09-19
From System->Administation->Login Window you can set an account to automatically login, under "Security'. I'd recommend using a TIMED login of a user account that doesn't have "admin" privileges.

---

### Post by jamvegan on 2007-09-19
Assuming that you are the user who was created during the installation of Ubuntu, you will have full access to all files and directories of every user on the system (via sudo).  When you create new users, if you do not want them to have access to other users' files and directories then make sure that they are not in the admin group.  This will also mean that they cannot perform system-wide functions such as installing new software (if they know what they are doing, they can install software within their own home directory, but not into the system directories where it would normally be installed).

To create a new user, go to System->Administration->Users and Groups, click Add User, and fill in the information for the new user.  You'll want to choose the Desktop User profile, most likely.  To see what that does and does not allow, click the User Privileges tab.  You can uncheck anything that you don't want them to have access to (and note that by default Administer the system is not checked for this profile).

After creating the user, you can do as lisati suggests.

---

### Post by stumped on 2007-09-19
Thank you both very much. This is exactly what I was looking for and it worked great.

---

