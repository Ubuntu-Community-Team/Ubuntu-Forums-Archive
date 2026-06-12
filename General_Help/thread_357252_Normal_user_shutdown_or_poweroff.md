---
title: "Normal user shutdown or poweroff"
date: 2007-02-09
forum: General Help
---

### Post by Titus A Duxass on 2007-02-09
How can I as a normal user use shutdown or poweroff from the command line without having to enter the sudo passwd?

The command in /sbin is for root only, changing permissions does not make any difference.

The same question was raised for Hoary, but there was no positive outcome.

---

### Post by Haegin on 2007-02-09
Theory says you add stuff to /etc/sudoers to give your user permissions but the guide I found didn't work.
To edit the sudoers file you have to use ```
sudo visudo
``` as that checks the file is ok (so you can't break root access on the machine!)
I will research more tonight and post it here.

---

### Post by Haegin on 2007-02-09
As far as I can tell this should work - you need to add the three aliases into the Cmnd Alias specification section (which is already there) and then add the last line in the user privilege specification section (which also already exists) putting you username in the correct place.

This has not been thoroughly tested as i had root privs when editing the file which persisted till I shut down a few mins later. Hopefully it will at least give somewhere to start.

The format is simply
<username> <machine name or ip - we are using ALL> <permissions>

```
# Cmnd alias specification
Cmnd_Alias      SHUTDOWN = /sbin/shutdown
Cmnd_Alias      HALT = /sbin/halt
Cmnd_Alias      REBOOT = /sbin/reboot

# User privilege specification
user-name-here   ALL=(ALL) NOPASSWD: SHUTDOWN, HALT, REBOOT

```

---

### Post by Titus A Duxass on 2007-02-10
I did not have any success with modifying sudoers.

I found a bit of information that suggested creating an /etc/shutdown.allow file with the user name in it, again no success.

---

### Post by Haegin on 2007-02-11
I have worked out how to do this and written up a wiki article covering the sudoers file and how to edit it including how to let yourself run shutdown commands without a password.
The whole article should give an understanding of the file but the stuff you are interested in is down near the end.
[https://wiki.ubuntu.com/Sudoers](https://wiki.ubuntu.com/Sudoers)

---

### Post by Titus A Duxass on 2007-02-11
Okay, thanks for your efforts.
I still am not allowed to shutdown from the terminal as a normal user.

Here is my sudoers file:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification
User_Alias USERS = mythtv

# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/halt, /sbin/reboot, /sbin/poweroff

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mythtv mythbox = NOPASSWD: SHUTDOWN_CMDS

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
mythtv ALL = (ALL) NOPASSWD: SHUTDOWN_CMDS

Can you see where the problem is?

Thanks

---

### Post by Haegin on 2007-02-11
Try removing the spaces in "ALL = (ALL)". I will update the guide if that is the problem but otherwise I don't know - I assume your main user is called mythtv and they are in the admin group. Also the line 
```
mythtv mythbox = NOPASSWD: SHUTDOWN_CMDS
```
is doing nothing so you can get rid of it. It is overridden by the line beginning "%admin" later in the file.

---

