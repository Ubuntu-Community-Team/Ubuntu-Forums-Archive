---
title: "[xubuntu] gpg4usb: Installation"
date: 2017-07-31
forum: General Help
---

### Post by ljubinski on 2017-07-31
Hello, me being a newbie - tried to install gpg4usb. should be the easiest of exercises , but.. there is the start_linux_32 bit directory, which i doubleclick and then there is the question with what application i want to open it. i thought this is already the executable file itself.    can anyone help with this?  Tank you!    (i found no realated forum/thread, and i hope this room is the right one for my question)

---

### Post by again? on 2017-07-31
Sounds like the file needs to be given permissions to execute.
You can do this by right clicking on the executable in the file manager.
Properties>permissions and ticking "Allow executing file as a program" or similar.

You can also do this via terminal.(The path to your executable may differ from mine)
eg
```
chmod +x ~/Downloads/gpg4usb/start_linux_64bit
```

---

### Post by ljubinski on 2017-08-01
Thank you! You are right, i failed first in giving the permission to execute, because the directory was on an USB flash drive. after moving it to HDD it worked.  Merci!

---

