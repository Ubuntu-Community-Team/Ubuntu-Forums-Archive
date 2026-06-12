---
title: "Added new user- no colors in shell"
date: 2008-03-28
forum: General Help
---

### Post by tcpip4lyfe on 2008-03-28
I added a couple users at work using this command:

useradd -d /home/newuser -M -s /bin/bash -G admin newuser

It works but I'm not getting the colors over SSH like when I log in with my admin user.   For example directories aren't blue, executables aren't green.  They are all the same color. su admin and I have a "normal" shell.   I assume this is a problem with what shell I used.  What shell has the colors?

---

### Post by markjensen on 2008-03-28
You might be looking for information on .dir_colors and/or .bashrc
[http://www.systhread.net/texts/200703bashish.php](http://www.systhread.net/texts/200703bashish.php)

---

