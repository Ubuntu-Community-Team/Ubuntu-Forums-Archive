---
title: "Telegram only launches as sudo"
date: 2018-03-31
forum: General Help
---

### Post by cehonski on 2018-03-31
Hello,

  I installed the telegram program under LXDE.  The only way it will launch is from the terminal using "sudo".  I have changed permissions on the executable and .desktop file using pcmanfm.  If I launch dolphin as sudo, then click the file from dolpin it launches.

---

### Post by #&amp;thj^% on 2018-03-31
> **cehonski said:**
> Hello,

  I installed the telegram program under LXDE.  The only way it will launch is from the terminal using "sudo".  I have changed permissions on the executable and .desktop file using pcmanfm.  If I launch dolphin as sudo, then click the file from dolpin it launches.

This is highly discouraged:
>  **If I launch dolphin as sudo, **then click the file from dolpin it launches. 

you show that you did run telegram as root, and it created the log file (as root), now, the regular user cannot write to the root-owned log file.

The problem is directory ownership. Fix it with 
```
sudo chown -R $(id -u:$(id -g) /home/"yourusername"/.local/
```
and **don't run graphics tools as root**. ;)
[U]BTW the "yourusername" is replaced with your user name.(Login Name)
[/U]
Now if that dose not fix it you just may have to remove/uninstall the Telegram Desktop completely, then remove the following directory:
```

~/.local/share/TelegramDesktop/log_startXX.txt
```
Please have a look here for admin right's with "to run a graphical command" : [https://askubuntu.com/questions/164819/how-can-i-run-an-application-with-a-gui-as-admin-from-a-non-admin-user-session](https://askubuntu.com/questions/164819/how-can-i-run-an-application-with-a-gui-as-admin-from-a-non-admin-user-session)

---

