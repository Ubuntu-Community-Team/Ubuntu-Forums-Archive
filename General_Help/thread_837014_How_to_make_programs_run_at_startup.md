---
title: "How to make programs run at startup?"
date: 2008-06-22
forum: General Help
---

### Post by zakeen on 2008-06-22
How to make programs run at startup?

thanks.

---

### Post by bmac on 2008-06-22
system/preferences/sessions/startup programs tab/"ADD"

Hope this helps....

---

### Post by caljohnsmith on 2008-06-22
Using the Sessions program as mentioned is great for running programs under your username at startup, but if you need to run a program on startup as root for some reason, just put it in the /etc/rc.local file.

---

### Post by zakeen on 2008-06-23
Thanks for all of this!

---

### Post by lutchezar on 2008-06-23
I'm using Ubuntu /Alternative/ as OS for thin station. I have no Desktop, just clean X server and client. Starting X with "startx" or "xinit" brings me only xterm, and i want just to execute Remote Desktop Client - how can i do that?
And is there any way to auto login without installing dektop just for starting X?

---

### Post by sujoy on 2008-06-23
> **lutchezar said:**
> I'm using Ubuntu /Alternative/ as OS for thin station. I have no Desktop, just clean X server and client. Starting X with "startx" or "xinit" brings me only xterm, and i want just to execute Remote Desktop Client - how can i do that?
And is there any way to auto login without installing dektop just for starting X?

place the program's name in your .bashrc, as for login check post no 11 [here]("http://ubuntuforums.org/showthread.php?t=680000&page=2")

---

### Post by lutchezar on 2008-06-23
thanks. And what about automatic shuttdown after programs end?

---

### Post by sujoy on 2008-06-23
i can only think of a workaround here.
first you need to add

%your_group_name ALL=NOPASSWD:/sbin/shutdown -h now

in /etc/sudoers (use sudo visudo to edit it), so that shutdown doesn't require password.

then you can just write a one line script that starts the program and calls shutdown when the program ends.

#!/bin/bash

urxvt -e program_name;shutdown




depends on what program you want to run.

---

### Post by lutchezar on 2008-06-23
Placing rdesktop brings a message"failed to open display" because of running before starting X.
Temporary I installed gnome /turn autologin on/ and  in ~/.xsession added line
"rdesktop -g 100% 192.168.1.141" and other ip-s so it worked.
Now I'm going to test shutdown after exiting from remote resktop.

---

