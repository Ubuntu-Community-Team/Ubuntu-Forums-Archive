---
title: "How can I delay user log-in until all init tasks are completed?"
date: 2015-01-08
forum: General Help
---

### Post by ianmaciel on 2015-01-08
I need to extract a file into user's home folder before he is able to log-in...


I've implemented that through a script located in /etc/rc2.d/.
The script works fine if I try to run it from a terminal. It is also correctly fired on system init, but the problem is that it still running after user log-in. The initialization is not waiting for this task to be completed.


So how can I guarantee that everything has been loaded before continue system initialization?

---

### Post by kpatz on 2015-01-08
Have your script create a file /etc/nologin when it starts and then remove it when it finishes.

---

### Post by ianmaciel on 2015-01-08
> **kpatz said:**
> Have your script create a file /etc/nologin when it starts and then remove it when it finishes.

Thank you for your reply.
It wasn't... I've just done what you suggested but it didn't work. The user a logged in and I can see the file "/etc/nologin".

The user is not actually log-in with password because it has "nopasswdlogin" enabled. So might need to delay other boot process to prevent window manager be loaded before my tasks is completed.

---

### Post by kpatz on 2015-01-08
Looks like /etc/init/lightdm.conf is the script that starts the GUI in Ubuntu.  Try calling your script from within there, before the line that reads "exec lightdm".  Then your script will run before X does.

---

### Post by ianmaciel on 2015-01-08
Yeah! It works!

:)

Thanks a lot for your help.

---

