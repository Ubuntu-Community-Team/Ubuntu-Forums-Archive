---
title: "Create an user with limited permission on Lubuntu"
date: 2016-10-20
forum: General Help
---

### Post by sed_faster on 2016-10-20
Hello folks,

I pretend install Lubuntu 16.04 LTS in pc for any employer use this pc! I think create an user with, only, permission to read and write, 770. 
This is the best scenario?
I think create this user through terminal, because I pretend create a script, and I don't where wizard has install on system for create and delete users!

I pretend disable Lubuntu Software Center, because I don't want which employers can install programs. This is the best shot?

I read, some here which, for a system more security, should change some relative with sudo and su! I can remember well about this! Any have an idea what can or should do relative with the su / sudo for the system be more security?

---

### Post by Impavidus on 2016-10-21
When you create a user through the GUI, you can choose what permissions he has. He can be an administrator, meaning he can use sudo and do everything, or he can be a normal user, who cannot change any system-wide settings, or you can use custom settings. From the command line you can assign the new user to various groups to get the same effect.

A normal user cannot run the Software Centre, or at least, cannot use it to install anything (he may be able to view the list of installed or available packages). A normal user can always install software in his own home directory, but this can never affect things outside his home directory.

---

