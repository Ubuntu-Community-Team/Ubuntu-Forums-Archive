---
title: "I cant transfer a file from my home to my computer"
date: 2015-12-16
forum: General Help
---

### Post by Ethan_Howarth on 2015-12-16
Look at the screenshots attached and see if you can figure it out for me.

Thanks,

(BTW im a noob to linux)

---

### Post by ian-weisser on 2015-12-16
Welcome to the forums.

A bit of explanation would be helpful.
It's not clear where you are trying to move the file from/to. From /home to /? (If so, why?)

And 'Show more details' on the error message, often explains the problem. Please tell us that complete, exact error message.

---

### Post by mojo-jar on 2015-12-16
In order to move a file or folder to the root directory you have to have 'root' permissions.

Please check the manual by entering 'man sudo' into a terminal.

Good luck and have fun.

---

### Post by buzzingrobot on 2015-12-16
Linux, like Unix before it, is a multi-user system.  That means one system can have multiple user accounts and that, if the hardware is set up appropriately, all those users can use that system simultaneously.

To prevent any one user from interfering with the folders, files, etc., of another user, Linux implements a system of permissions and privileges.  Each user gets a "home" directory bearing his or her user name.  That user has full access to that directory. 

The "Computer" is a label the file manager applies to the directory structure that ordinary users lack permission to change.  It is, in reality, the "/" directory and its contents. The error message from the file manager is telling you that you are trying to do something that you, as an ordinary user, are not authorized to do. 

Unless you have experience and know exactly what you are doing there is no reason to store files in any location outside your home directory.  The system expects to find certain files in certain places, and if you accidentally delete, move or alter one of them, you can disable the entire system.

---

