---
title: "Alow user to log in to terminal only"
date: 2016-03-26
forum: General Help
---

### Post by sander13 on 2016-03-26
Hey guys i am new to the forums here and wanted to ask something and please feel free to move my post if it isn't in the right section

How do i disable the/a GUI for a specific user so he/she can only log in with terminal

Thanks in advance

---

### Post by TheFu on 2016-03-27
Welcome to the forums.

Disable the GUI for everyone.  Remove the X11 server.  If you allow login to the system and don't completely lock down the system to prevent all write access to their HOME and even /tmp, then that userid can install whatever they want and run it.  Unix is about power-to-the-end-users. That is part of the system design.  Heck, even if you only allow access from a remote system through ssh, the user could still install and run a remote desktop like x2go into their HOME.

Now, if you just want to make it difficult for end users, you can force a non-GUI login for everyone, but they'd still be able to "startx" and get a GUI, if you don't remove the X11 code.

To provide any option, we need to know the specific version of Ubuntu being used.  Startup techniques have radically changed between 14.04 and later releases.  [https://askubuntu.com/questions/16371/how-do-i-disable-x-at-boot-time-so-that-the-system-boots-in-text-mode](https://askubuntu.com/questions/16371/how-do-i-disable-x-at-boot-time-so-that-the-system-boots-in-text-mode) is one answer.  Note that this does impact all userids.

---

