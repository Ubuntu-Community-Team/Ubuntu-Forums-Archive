---
title: "Manual reboot using init 6"
date: 2016-06-24
forum: General Help
---

### Post by pfeiffep on 2016-06-24
I've been using a terminal for updating / upgrading my Ubuntu MATE 16.04 since official release and find it easier to manually reboot using```
 sudo init 6
``` Once a while ago I forgot the sudo and was very surprised that the system rebooted. I decided to test whether this was present in vanilla Ubuntu 16.04 using these steps in a virtual environment:

[LIST]
[*]fresh install 
[*]first boot no update - upgrade 
[*]init 6 reboots - **no sudo required** 
[*]performed updat upgrade 
[*]created standard user 
[*]logout and login as standard user 
[*]init 6 reboots - **no sudo required** 
[/LIST]
For my single user system this is not a concern, however **this is certainly wrong!**

---

### Post by pfeiffep on 2016-06-26
Direct copy from an answer to my question posed on Ask Ubuntu ... this sounds technically correct, but I question the wisdom
  ```
It is a design feature that since 16.04 you do no longer need root privileges to shut down or reboot the system through any method.
Instead the systemd and its systemctl tool accept those commands from regular users.

All related commands like shutdown, reboot, halt, poweroff are  symbolic links ("symlinks") to /bin/systemctl and init is a symlink to  /lib/systemd/systemd now by the way. 
You can verify this using the  command file $(which COMMAND), replacing "COMMAND" with the one you want  to check.

```[INDENT]  

[/INDENT]
A standard desktop user is also able to execute these commands with sudo. 
The good news is **if another user is logged in the commands won't work without sudo.**

---

